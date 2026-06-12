---
title: "Ramdisk issues"
date: 2014-03-03
forum: General Help
---

### Post by Elochai on 2014-03-03
Hello,

I am trying to install and run my game server using the RAM as a ramdisk.

I understand that the ./dev/shm location will allow me to do this.


Issue I am having is that when I install the files into a folder within the shm folder and run my command line to start the gaming server, it doesn't work. The gaming sever will come back with an error saying it can't find the file for starting the server, yet the file is there, path is right, and from what I can tell the permissions seem right.


Any reason I can't run my game server / application from with in shm ? or any ideas on how I can get this to work ?

---

### Post by Jason_Gibson on 2014-03-03
You can mount a ramdisk anywhere you want. I personally put mine for Minecraft at /media/ramdisk. Somehow doing anything in / outside of /home and /media seems a bad idea to me though. That may be the issue altogether. 

Maybe you need to link it properly? I had a script copy my .minecraft folder into the ramdisk on boot and make a backup every 10 minutes. But I had to put a link from /media/ramdisk/.minecraft > ~/.minecraft. If it is expecting everything to be in a certain place and you don't have it linked it won't work.

---

### Post by Elochai on 2014-03-04
I tried making a ramdisk outside of home with bad results as well. When I get home I'll login to the server and try creating a ramdisk inside home. 

It not minecraft but a FPS game. I was thinking the ramdisk method would be best as I got 32 GB of ram and the game will only need about 3 GB. This should make things run more smooth and faster when it comes to map loads, and player data writing and reading.

---

### Post by Elochai on 2014-03-05
Ok I created a ramdisk inside my home folder.

Worked perfectly !

And running the game, you can tell it very smooth as all actions play without any form of lag. Which is great as this game AI spawning mass can make little lag spikes on data writing.

I love the performance so much, I may try it on another game I run that tends to read and write non-stop plus loads large map files.


Only one question. When I go to system monitor, I still shows all my ram and what being used by the servers. It doesn't show 3GB of ram missing for the ramdisk. Is this normal ?

---

