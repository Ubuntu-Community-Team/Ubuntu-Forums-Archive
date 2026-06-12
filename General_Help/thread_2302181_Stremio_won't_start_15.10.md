---
title: "Stremio won't start 15.10"
date: 2015-11-08
forum: General Help
---

### Post by David_Medeiros on 2015-11-08
So, yesterday Stremio was fine. Today asked for an update. Asked me to relaunch and then it never opened again. I decided to remove it an download again. And still all it shows is this.

[HTML]david@UBook:~/Stremio$ sudo ./Stremio-runtime [9890:1108/154211:ERROR:browser_main_loop.cc(189)] Running without the SUID sandbox! See https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment for more information on developing with the sandbox on.
[9924:1108/154212:INFO:renderer_main.cc(200)] Renderer process started
[9890:1108/154212:WARNING:accelerator_util.cc(118)] Invalid accelerator token: command
[9890:1108/154212:WARNING:accelerator_util.cc(118)] Invalid accelerator token: command
[9890:1108/154212:WARNING:accelerator_util.cc(118)] Invalid accelerator token: command
[9890:1108/154212:WARNING:accelerator_util.cc(118)] Invalid accelerator token: command
ffmpeg located -> undefined
{ [Error: listen EADDRINUSE :::11474]
  code: 'EADDRINUSE',
  errno: 'EADDRINUSE',
  syscall: 'listen',
  address: '::',
  port: 11474 }
[9890:1108/154213:INFO:CONSOLE(1)] "Error: EACCES: permission denied, open '/home/david/.config/stremio/.linvo-user'", source: /home/david/Stremio/resources/app.asar/node_modules/linvo-api4-client/client.js (1)
[9890:1108/154214:INFO:CONSOLE(1)] "Unable to load WebChimera.js", source: file:///home/david/Stremio/resources/app.asar/blob.js (1)
[9890:1108/154214:INFO:CONSOLE(1)] "Error: Cannot find module 'wcjs-prebuilt'", source: file:///home/david/Stremio/resources/app.asar/blob.js (1)
[9890:1108/154214:INFO:CONSOLE(1)] "ReferenceError: mixpanel is not defined
    at new vlcDevice (file:///home/david/Stremio/resources/app.asar/blob.js:1:233)
    at Object.<anonymous> (file:///home/david/Stremio/resources/app.asar/blob.js:2:25211)
    at Object.e [as invoke] (file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:39:193)
    at Object.$get (file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:37:98)
    at Object.e [as invoke] (file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:39:193)
    at file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:41:10
    at d (file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:38:394)
    at Object.e [as invoke] (file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:39:161)
    at file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:41:57
    at m (file:///home/david/Stremio/resources/app.asar/bower_components/angular/angular.min.js:7:322)", source: file:///home/david/Stremio/resources/app.asar/blob.js (1)
[9890:1108/154214:INFO:CONSOLE(1)] "TypeError: Cannot read property 'get' of undefined
    at http://www.strem.io/cinematicDoor.js:75:35", source: file:///home/david/Stremio/resources/app.asar/blob.js (1)

[/HTML]


Have no idea what to do. I am searching but i think i need some help here.

---

### Post by David_Medeiros on 2015-11-08
Solved. All i had to do is start Stremio throug Stremio.sh and not Stremio-runtime like i used to do before the update. So, if anyone is having the same problem that i had. Just put Stremio folder in home (opcional) and change the name to Stremio. Then open the terminal and type the following:
[html]cd Stremio/[/html]
[html]./Stremio.sh[/html]
done!

---

