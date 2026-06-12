---
title: "Ubuntu 13.04 windows title bar not clickable"
date: 2013-04-26
forum: General Help
---

### Post by cruz12141214 on 2013-04-26
hello all:

there is a problem that i have noticed ( i know Ubuntu 13.04 just came out but im just making this error known just in case)

While using compiz on the gnome-session-fallback

for windows that open maximized: 

the windows title bars are not responding to mouse clicks, it seems that the click goes to the desktop or any working windows right under it, 

as if the title bar does not exist 
only way to fix is to not start maximised or de maximise using some means 

this should be 100% reproducable

with compiz CCSM login to the gnome session fallback

open a maximized window and see what happens 

I cant post an error report as the apport does not catch anything pertaining to it

my RIG:

Asus g74sx

Ubuntu 13.04 x 64 
Session: gnome session fallback 
Nvidia piority drivers for gtx 560m 2gb vram
8gb ram
core i7 2 gen

---

### Post by dino99 on 2013-04-26
you need to hold "Alt" key down first

---

### Post by cruz12141214 on 2013-04-26
oh that does not even work ive tried, and yes all the options that need to be enabled on compiz are enabled

the only way i can move the window is by grabing it under the title bar when this happens

---

### Post by CatKiller on 2013-04-26
I've experienced the same, on 12.10 with Compiz Experimental installed. Meant to file a bug report but haven't got round to it.

Haven't found a good workaround other than unmaximising from the task manager first. It can be quite irritating to have a random window close unexpectedly.

---

### Post by cruz12141214 on 2013-04-26
yes it is very irritating, this only happens on the gnome session fall back, it does not happen on unity (which i dont like using)

---

### Post by CatKiller on 2013-04-26
I'm not using Unity either, for the same reason.

---

### Post by cruz12141214 on 2013-04-26
I guess i have to put up with unity till tis issue is fixed

---

### Post by CatKiller on 2013-04-27
Other desktops and window managers are available - it doesn't have to be Unity. Personally, I'd rather put up with the bug than use Unity :)

---

### Post by CatKiller on 2013-04-27
Actually, mine seems to have fixed itself. Fingers crossed for you.

---

### Post by pqwoerituytrueiwoq on 2013-04-27
i believe this thread is relevant:
[http://ubuntuforums.org/showthread.php?t=2127673](http://ubuntuforums.org/showthread.php?t=2127673)

---

### Post by cruz12141214 on 2013-04-27
yes it is, but in my case its when a window starts maximized, 

 and its fixed when i find some way to minimize, ALT does not help


IE the cause is different but the symtoms such as the layer thing are the same


I did not have this issue with any other Ubuntu release

---

### Post by Calluin on 2013-05-06
This is a confirmed compiz bug. It is pretty annoying, so I hope it will rise in urgency soon and get fixed :-)
[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

---

### Post by GyozaGuy on 2013-05-28
I have this problem too, and while it is a bit frustrating, I have found that I can get around it quickly by holding down ALT, clicking anywhere on the window, then dragging the window down and back up again quickly.  I guess this only works if the Compiz "Move Windows" plugin is enabled, but it isn't too annoying to do quickly.

---

### Post by pennstatebadboy on 2013-06-05
Has anyone been able to fix this yet? I keep accidentally closing the window behind the window I'm viewing.

My best workaround is to use the **SUPER+M** key combination, which I think unmaximumizes the window enough that the window buttons work.

---

### Post by ronaldv on 2013-06-29
same issue here. Hope it gets fixed soon.

Also I see that sometime the gnome-fallback process is using vert high cpu. Do you see this too?

---

### Post by pennstatebadboy on 2013-07-15
Has anyone found a solution to this issue yet?

---

### Post by sage79 on 2013-09-08
[https://launchpad.net/~a7x/+archive/bug1158267](https://launchpad.net/~a7x/+archive/bug1158267)
Here is the solution.
For me works

---

