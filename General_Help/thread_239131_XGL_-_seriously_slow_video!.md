---
title: "XGL - seriously slow video!"
date: 2006-08-18
forum: General Help
---

### Post by OMRebel on 2006-08-18
I just installed XGL on my PC, and the video is just horribly slow.  I have a Radeon 9600SE (128MB).  Please help. ](*,)

---

### Post by OMRebel on 2006-08-18
Some additional information:
brad@ubuntu:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
512 frames in 6.5 seconds = 78.272 FPS
360 frames in 5.7 seconds = 63.055 FPS

---

### Post by angkor on 2006-08-18
What player are you using? Try mplayer with the gl2 video output:

```
mplayer -vo gl2 {name-of-video}
```

---

### Post by OMRebel on 2006-08-18
I'm not using any player.  This is using any application.  When I launch FireFox, it now takes forever to open it.  Same with any other application I launch.  Is XGL just gonna be too much for my system to handle?  Everything was running very fast before.

---

### Post by yatt on 2006-08-18
> **OMRebel said:**
> I'm not using any player.  This is using any application.  When I launch FireFox, it now takes forever to open it.  Same with any other application I launch.  Is XGL just gonna be too much for my system to handle?  Everything was running very fast before.

Try typing this in a terminal:
```
fglrxinfo
```
Then post the results.

---

### Post by OMRebel on 2006-08-18
I get:
Error: unable to open display :0

---

### Post by yatt on 2006-08-18
> **OMRebel said:**
> I get:
Error: unable to open display :0

Are you able to do regular gnome sessions? If you can try running fglrxinfo in one of them.

---

### Post by OMRebel on 2006-08-18
Not sure how to go back.  I disabled the /usr/bin/startcompiz in my Startup.  I had followed the instructions on getting it setup from here:

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Now, one thing I should point out is that step that says to edit the gdm.conf and change GdmXserverTimeout=10 to 50 <--- that line wasn't in my original gdm.conf, but I added it anyways.  Could that be the problem?

---

### Post by yatt on 2006-08-18
> **OMRebel said:**
> Not sure how to go back.  I disabled the /usr/bin/startcompiz in my Startup.  I had followed the instructions on getting it setup from here:

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Now, one thing I should point out is that step that says to edit the gdm.conf and change GdmXserverTimeout=10 to 50 <--- that line wasn't in my original gdm.conf, but I added it anyways.  Could that be the problem?

Nope, that tells GDM how long to wait before giving up on loading. Though it is surprising not to see it there. You should use Gedit to search for it and see if you got a duplicate...

The method you use runs GDM as on XGL. This made my computer pretty slow too (and I have a Radeon X1800). As I have had problems with method one, I do suggest method two.

---

### Post by OMRebel on 2006-08-18
Thanks.  I'll try out that second method.  I really do appreciate your time and help on this.  The Ubuntu community rocks!

---

### Post by yatt on 2006-08-18
> **OMRebel said:**
> Thanks.  I'll try out that second method.  I really do appreciate your time and help on this.  The Ubuntu community rocks!

I *think* you only need to udo the changes to /etc/gdm/gdm.conf-custom and /etc/gdm/gdm.conf then create the scripts in method two.

---

### Post by OMRebel on 2006-08-19
I did step 2, and it runs really good now.  

My only problem now is that I don't the the minimize, maximize, or close buttons on the top of any of my applications anymore??  How can I get that back?  In other words, the title bar is gone.  ????????????

---

### Post by AirRaven on 2006-08-19
> **OMRebel said:**
> I did step 2, and it runs really good now.  

My only problem now is that I don't the the minimize, maximize, or close buttons on the top of any of my applications anymore??  How can I get that back?  In other words, the title bar is gone.  ????????????

Do you mean that the title bar itself is gone? The whole decoration? Or is it just blank with no buttons, but the bar's still there?

If you have no bar whatsoever, then you need to try running cgwd. If you have a bar, then you need to replace all mentions of "gnome-window-decorator" in your startup script with "cgwd".

---

### Post by Patrick-Ruff on 2006-08-19
use glxinfo instead of fglrxinfo, it rarly works. glxinfo is the only one that gives you the complete info. also, direct rendering is normally not working so if you see that its not your problem. but if you see Mesa, then you have a problem ;)

---

### Post by yatt on 2006-08-20
> **AirRaven said:**
> Do you mean that the title bar itself is gone? The whole decoration? Or is it just blank with no buttons, but the bar's still there?

If you have no bar whatsoever, then you need to try running cgwd. If you have a bar, then you need to replace all mentions of "gnome-window-decorator" in your startup script with "cgwd".

You have to install it from the repos first.

---

