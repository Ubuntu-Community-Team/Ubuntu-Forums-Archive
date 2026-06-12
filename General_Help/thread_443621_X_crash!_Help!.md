---
title: "X crash! Help!"
date: 2007-05-14
forum: General Help
---

### Post by Ankher on 2007-05-14
Okay, a few days ago I noticed that my screen resolution was back down to 1024x768 (or something like that). My monitor is usually at 1280x1024, and so I thought this was weird b/c I had to add "1280x1024" on a bunch of lines to /etc/X11/xorg.conf So I open and close xorg.conf, and see if the "1280x1024" is still there. It is.

I uninstall nvidia-glx and install nvidia-glx-new (don't ask me why, I assumed that that would be better). I restart X (or my computer) and it crashes. It says to check if the NVIDIA files are set up correctly and whatever. I can't get a GUI. Is there a way to fix this from a tty session? (maybe a new xorg.conf file?) GAAH!

---

### Post by taurus on 2007-05-14
Boot into recovery mode and 

1.  Edit /etc/X11/xorg.conf and change the Driver from "nvidia" back to "nv".

```
nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

or

2.  Reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Ankher on 2007-05-16
Great! Thanks!

Okay, that gets my X up and running. But I have a small problem: I kinda like running Beryl, having fast scroll downs (not repaints!!) Anyways

I uninstalled and reinstalled the nVidia driver via Add/Remove programs. It griped about dansguardian and since I can't get it to work, I uninstalled it (was going to anyway). Uninstalled and reinstalled again, seemed to be running fine. So I type ```
sudo nvidia-glx-config enable
``` to use the nVidia driver.

I restart X, everything seems to be going fine, except that I can't see my mouse. This has happened before when I restart X, and restarting the computer seems to clear the bug, so I do that. When it loads it gives me a tty login, which blinks a few times then goes to a really messed up blue-ish Text GUI, with a bunch of random characters outside the window in various places. It says something to the effect of X has crashed and would I like to see the output? I hit yes and after a bunch of preliminary griping I get this ```
(==) Log file: "var/log/Xorg.0.log", Time: Wed May 16 15:32:54 2007
(==) Using confige file: "etc/x11/xorg.conf"
Error: API mismatch: the NVIDIA kernel module has the version
1.0-9755, but
this X module has the version 1.0-9631. Please make sure that the
kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please
ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this
system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created
properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.
                                                         n.
Fatal server error:
 no screens found
```

That's as close to what I saw as possible.

So I run ```
sudo nano -Bw /etc/X11/xorg.conf
``` and change "nvidia" back to "nv" and reinstall the kernel and source of the kernel. Then I try it again. Same result. Then I run ```
sudo dpkg-reconfigure xserver-xorg
``` and give X all the right information I can get easily (the name/number thing of my graphics card, monitor, etc.)

My graphics card is an nVidia GeForce 6150 LE, I have the normal driver installed, this is okay, right? Anything anyone can do to help!

---

### Post by Ankher on 2007-05-17
Umm... hello?

---

