---
title: "I broke Ubuntu"
date: 2007-04-14
forum: General Help
---

### Post by kenboyles72 on 2007-04-14
I was running XMMS and clicked something on the xmms panel, I think it was writting (going up and down) on the left side of the player. Then part of my screen went crazy, like if you set the wrong resolution for your monitor. Hit ctrl+alt+backspace and rebboted. On reload, I get this error "Failed to start X server. It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?". I choose yes and check the log and see this error:

Could not open
/lib/modules/2.6.17-11-generic/volatile/nvidia.kko

Failed to load NVIDIA Kernel module

And then drops to terminal. Good thing I had it dual booted with XP, at least I can still run something. I was going to try to mod my xserver config file, but the drive that Ubuntu is on was formated ext3 and xp wont see it. Is there an easy fix for this?

---

### Post by taurus on 2007-04-14
Boot into recovery mode from GRUB menu and at the prompt, edit /etc/X11/xorg.conf

```
nano -Bw /etc/X11/xorg.conf
```
Scroll down until you get to

```
Driver        "nvidia"
```
and replace it with

```
Driver         "nv"
```
Save and exit with <Ctrl>o and <Ctrl>x.

Reboot and see if X is running again this time.

p.s.  If you need to access Ubuntu (ext3) from Windows, just install fs-driver, [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by kenboyles72 on 2007-04-14
ok, finally got it back running. I downloaded the Ext2 Installable File System for Windows. Edited the file and still got an error. So, I just deleted xorg.conf and renamed xorg.conf.bak and edited that file. Now how can I reconfig everything?

Edit:
And now I don't seem to have any open gl support. When my screensaver starts, it just shows a blank screen. When i go and choose a screensaver half of em don't show up.

---

### Post by taurus on 2007-04-14
Not sure what you mean by reconfigure everything.

---

### Post by kenboyles72 on 2007-04-14
how do I reconfig my system and graphics to get my openGL support back.

---

### Post by taurus on 2007-04-14
You are currently using nv driver so you need to install nvidia driver before you can get 3D out of it.  One way is to use envy.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

