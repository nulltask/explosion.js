# explosion.js
こいつは、ありとあらゆるサイトを爆発させるために作られました。  
ブックマークレットなので、いつでもサイトをぶっ壊せます。  
イライラした時のストレス発散に、  
誰かをびっくりさせたい時、  
何となく、  
どんなシチュエーションでも使えるでしょう。  
  
## How to Use?
↓をブックマークのURLとしたブックマークレットとしてお使いください。  

	javascript:(function(){if(!console||!console.log)console={log:function(){}};var s=document.createElement('script');s.type='text/javascript';s.src='https://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js';document.body.appendChild(s);if(window.THREE==null||window.THREE.DOMRenderer==null){s=document.createElement('script');s.type='text/javascript';s.onload=b;s.src='https://raw.github.com/mrdoob/three.js/r49/build/Three.js';document.body.appendChild(s);}else{b();}function b(){var $=jQuery.noConflict(true),camera=new THREE.PerspectiveCamera(60,window.innerWidth/window.innerHeight,1,1000000),scene=new THREE.Scene(),stage=new THREE.Object3D(),renderer=new THREE.DOMRenderer(),controls=null,clock=new THREE.Clock(),windowWidth=window.innerWidth,windowHeight=window.innerHeight,windowHalfWidth=windowWidth>>1,windowHalfHeigth=windowHeight>>1,body=$('body').css('overflow','hidden'),state=0,max=70,swf='https://shiftbrain.sakura.ne.jp/devjam/ssl/explosion.js/explosion.swf',sound=$('<object id=\'externalsound\' classid=\'clsid:d27cdb6e-ae6d-11cf-96b8-444553540000\' codebase=\'http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,0,0\' width=\'1\' height=\'1\'><param name=\'movie\' value=\''+swf+'\' /><param name=\'allowScriptAccess\' value=\'always\' /><embed name=\'externalsound\' src=\''+swf+'\' width=\'1\' height=\'1\' allowScriptAccess=\'always\' type=\'application/x-shockwave-flash\' pluginspage=\'http://www.macromedia.com/go/getflashplayer\' /></object>'),count=body.children().length;body.children().fadeOut(1500,init);function init(){count--;if(count!=0)return;window.scrollTo(0,0);scene.add(stage);scene.add(camera);$(window).bind('resize',resize);resize();camera.position.z=windowWidth*20;document.body.appendChild(renderer.domElement);body.find('img').each(toThreeJs);if(count<max)body.find('a').each(toThreeJs);if(count<max)body.find('span').each(toThreeJs);if(count<max)body.find('p').each(toThreeJs);sound.appendTo('body');setTimeout(function(){state=1;},500);update();requestAnimationFrame(update);}function toThreeJs(){if(count>=max)return;var p=new THREE.Particle(new THREE.ParticleDOMMaterial($(this).css('position','absolute').appendTo('body').get(0)));p.position.set(Math.random()*windowWidth-windowHalfWidth,Math.random()*windowHeight-windowHalfHeigth,Math.random()*windowWidth-windowHalfWidth);stage.add(p);count++;}function update(){if(state==1)explosion();else if(state==2)waft();renderer.render(scene,camera);requestAnimationFrame(update);}function explosion(){stage.rotation.y+=0.005;camera.position.z+=(windowHalfWidth-camera.position.z)*0.3;if(Math.abs(windowHalfWidth-camera.position.z)<0.1){body.css('cursor','move');controls=new THREE.TrackballControls(camera);state=2;}}function waft(){stage.rotation.y+=0.005;controls.update(clock.getDelta());}function resize(){renderer.setSize(window.innerWidth,window.innerHeight);}}})();
  
## Changelog
* _2012.08.09_ - 爆発音追加。githubに置いたファイルだと鳴らなかった。mime関連かな？
* _2012.08.09_ - とりあえずアップ。

## Credits
@kaminaly

