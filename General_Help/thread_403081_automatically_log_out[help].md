---
title: "automatically log out[help]"
date: 2007-04-06
forum: General Help
---

### Post by gtcoffee on 2007-04-06
hi...i don't know y it will automatically log out when i'm idle for awhile...
how to fix this???

thanks for helping..

---

### Post by kidders on 2007-04-07
Hi there,

I can't help wondering if what's really happening is that your X server is restarting. Perhaps something power-related (or a screensaver) is crashing X. This is just a wild guess, but do your system logs suggest anything like that, by any chance?

---

### Post by Wim Sturkenboom on 2007-04-07
Do you need username and password or only password. In the latter case, it's the automatuc screen lock.

---

### Post by Traks on 2007-04-07
I had a similar issue and it was Nvidia and GLX problems from the latest update.  I was able to resolve my issue by:

From astoltz in  [http://ubuntuforums.org/showthread.php?t=403164](http://ubuntuforums.org/showthread.php?t=403164)


> From the command line it's:

```
cd /usr/lib/xorg/modules/extensions/
sudo mv libglx.so libglx.so.backup
sudo ln -s libglx.so.1.0.9755 libglx.so
```


Then either a reboot or just re-start X with ctrl-alt-backspace
Reply With Quote

---

### Post by kidders on 2007-04-08
> **Traks said:**
> I had a similar issue and it was Nvidia and GLX problems from the latest update.
The latest update seems to be causing problems for many people. :-( This fix should work if gtcoffee can confirm he's using an OpenGL screensaver, for instance.

---

### Post by graphicw on 2007-04-09
I had the same problem with the random X restarts, especially when using any applications that used 3D features.  The above fix resolved my issue.  Thanks for posting it.

---

### Post by ckoester on 2007-05-04
I'm having the same problem.  It started happening after I attempted to change my screensaver.  When the screensaver starts it automatically logs me out.  If I attempt to change the screensaver it abruptly crashes my X session.

I tried reinstalling gnome-screensaver but that did not work.  I'm going to try manually changing the screensaver...

---

