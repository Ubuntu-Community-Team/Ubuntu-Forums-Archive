---
title: "Gimp is memory hungry"
date: 2005-03-21
forum: General Help
---

### Post by bigzak on 2005-03-21
I recently (yesterday) upgraded to HH preview, and I'm well impressed. Even my old scanner has jumped into life! Unfortunately, all is not well. While I'm glad the Gimp is finally at 2.2, it has some memory management issues.

On several occassions I have tried to start a filter (usually unsharp mask or gaussian blur) and received a 'cannot allocate memory' error. Any attempt to save to any format after this results in a segfault.

On other tries, I have successfully edited and saved a couple of images, then tried to load a third, only for the Gimp to thrash itself (and my PC) to death, with only a cold power down stopping the madness. I'm not sure if it's a memory issue (and hence swap thrashing) or a CPU/caching issue as I've never managed to get the machine to respond once it begins.

Has anyone else experienced this? I am editing images from my 4Mpixel digicam, so they are about 2200x1700 in size, although I have never had trouble with Gimp 2.0 under Ubuntu or 2.2 under Slackware.

---

### Post by Glanz on 2005-03-21
You will have to go to GIMP preferences and adjust the tile cache size, under "environment." This all depends upon how much RAM you have in your system. If you have RAM to spare, give it more. The less RAM, the more swap space will be used to compensate. I believe the more swap you use, the more disk thrashing occurs because swap isn't static and RAM is silently so.

Tile cache size This is the amount of system RAM allocated for GIMP image data. If GIMP requires more memory than this, it begins to swap to disk, which may in some circumstances cause a dramatic slowdown. You are given an opportunity to set this number when you install GIMP, but you can alter it here. See How to Set Your Tile Cache for more information.

---

### Post by bigzak on 2005-03-22
Thanks, I'll have a play with that setting. It certainly sounds like that could be the problem, although I've never experienced it with other versions. My laptop with Slackware on has the default configuration too, and that has half the RAM of my desktop and has no problems. Most odd.

---

