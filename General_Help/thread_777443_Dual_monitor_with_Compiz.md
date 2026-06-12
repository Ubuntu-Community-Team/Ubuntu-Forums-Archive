---
title: "Dual monitor with Compiz??"
date: 2008-05-01
forum: General Help
---

### Post by teejeaux on 2008-05-01
I've got a Dell D630 laptop that I use dual monitors with.  If I boot up and use the LCD on the laptop, Compiz works great, AWN works great, and I'm a happy camper.  As soon as I dock it, and run the dual monitors, Compiz and AWN stops working.  I think it's probably due to a limitation in video memory, but I was wondering if anyone has gotten this to work.

---

### Post by +Eric on 2008-05-02
Well, I can at least tell you I have dual monitors on my desktop and I have compiz running as well as AWN....

---

### Post by teejeaux on 2008-05-06
> **+Eric said:**
> Well, I can at least tell you I have dual monitors on my desktop and I have compiz running as well as AWN....

What kind of video card do you have? How are you running the dual monitors? Are they each a separate session? or are they like a single session across two monitors? Twinview or Xinerama?

Thanks!

---

### Post by RAOF on 2008-05-06
The problem is likely to be the maximum GL texture size, which for many cards (Intel, not-very-new ATI, really old nvidia) tends to be 2048x2048 (or even lower).  This limits your maximum combined resolution across all heads to 2048x2048, because the root window needs to span both.

---

### Post by CrazyGuy123 on 2008-05-06
If it's not that it could be video memory.  If it's using shared memory, it can usually be adjusted in the computer BIOS - you can get to that by turning off the laptop and turning it on again while tapping F2, F10, F12, Delete or escape (try each key in turn unless you have a manual about to say which key).  you should get to a menu - in one of the menus you'll find graphics or video memory (sometimes called shared memory). it usually adjusts between 1MB and 256MB - try setting it one click higher than it already is and see if it works then.

---

### Post by Ieatmacs on 2008-05-06
Did you fix this OP?

---

### Post by SEMW on 2008-05-06
This is a known limitation of X with certain graphics chips (especially Intel and ATi ones). See [https://wiki.ubuntu.com/X/Config:](https://wiki.ubuntu.com/X/Config:) "*Note that setting Virtual to larger than 2048x2048 disables 3d acceleration (i.e., no Compiz)*".  There is no solution as far as I know.

A workaround is to arrange the two monitors one *above* the other; since this will almost certainly not break the 2048x2048 barrier.  Whether this is an acceptable solution is up to you.

[IMG]http://www.thinkwiki.org/images/a/ac/Intel-DualHead.png[/IMG]

---

### Post by teejeaux on 2008-05-06
Ok, I just did some testing, and lowering the resolution to each having 1024X768 didn't fix it, in fact, it caused all kinds of errors.  Everything was fine when I went back to the native 1280X1024 on each.  This is my setup:

Computer: Dell D620
Video: Quadro NVS 110M
Video Mem: 256 MB
Monitor0: Dell 1907FP (Analog)
Monitor1: Dell 1908FP (Digital)

OS: Hardy Heron using the proprietary NVidia drivers.

I think I'm going to see if I can bump up the video RAM in the bios. I'll let you know how that goes.

Teejeaux

---

### Post by lukemack on 2008-05-14
I'm also seeing this problem. nVidia GeForce Go 7600 graphics chip on a Vaio laptop. Xinerama mode.

It works fine in single monitor mode.

---

### Post by teejeaux on 2008-05-14
> **SEMW said:**
> This is a known limitation of X with certain graphics chips (especially Intel and ATi ones). See [https://wiki.ubuntu.com/X/Config:](https://wiki.ubuntu.com/X/Config:) "*Note that setting Virtual to larger than 2048x2048 disables 3d acceleration (i.e., no Compiz)*".  There is no solution as far as I know.

A workaround is to arrange the two monitors one *above* the other; since this will almost certainly not break the 2048x2048 barrier.  Whether this is an acceptable solution is up to you.

[IMG]http://www.thinkwiki.org/images/a/ac/Intel-DualHead.png[/IMG]

I have a feeling you're right about this.  I've got two monitors set to 1280X1024, so this goes over the limit for sure.

Does anyone know of any way, or plans, to remove this limit??

Teejeaux

---

### Post by RAOF on 2008-05-14
> **lukemack said:**
> I'm also seeing this problem. nVidia GeForce Go 7600 graphics chip on a Vaio laptop. Xinerama mode.

It works fine in single monitor mode.

Different issue.  nVidia doesn't support Composite with Xinerama, so you can't run Compiz+Xinerama.  Use TwinView and it'll work.

> **teejeaux said:**
> I have a feeling you're right about this.  I've got two monitors set to 1280X1024, so this goes over the limit for sure.

Does anyone know of any way, or plans, to remove this limit??

Teejeaux

That is a hardware limit; there are (moderately evil) ways of working around it, but none are being actively developed as far as I know.  That said, I believe that your nVidia card has a limit of 4096x4096, which should support your dual-head fun.  What does running "glxinfo -l | grep -i max_texture_size" print out?

---

### Post by teejeaux on 2008-05-15
> **RAOF said:**
> 
That is a hardware limit; there are (moderately evil) ways of working around it, but none are being actively developed as far as I know.  That said, I believe that your nVidia card has a limit of 4096x4096, which should support your dual-head fun.  What does running "glxinfo -l | grep -i max_texture_size" print out?

GL_MAX_TEXTURE_SIZE = 4096

So for clarity sake:
OS: Hardy Heron
Video Card: nVidia Quadro NVS 110M
Driver: 169.12
Laptop: Dell D620
Dual Monitors: Dell 19" Flat Panels
Configured using Xinerama

Compiz and AWM work great when just running the laptop. When I've got it docked using the dual monitors, the advanced graphics don't work at all.

Thanks!

---

### Post by RAOF on 2008-05-16
> **teejeaux said:**
> GL_MAX_TEXTURE_SIZE = 4096
...
Configured using Xinerama
...

As above, there's your problem right there.  Again, nVidia don't support Xinerama+Composite.  Use TwinView and this will work.

An example xorg.conf using TwinView can be generated like so:
```

cp /etc/X11/xorg.conf ~/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig --twinview

```
Restart X and you should have dual-head goodness, and have Compiz working.

---

### Post by teejeaux on 2008-05-16
> **RAOF said:**
> As above, there's your problem right there.  Again, nVidia don't support Xinerama+Composite.  Use TwinView and this will work.

An example xorg.conf using TwinView can be generated like so:
```

cp /etc/X11/xorg.conf ~/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig --twinview

```
Restart X and you should have dual-head goodness, and have Compiz working.

But Twinview creates two completely different desktops, not a single desktop that covers both screens, correct? I don't want two different desktops. I use the two screens as a single screen, passing things back and forth, and sometimes I use them as a single screen and spread a window all the way across it.  Or maybe I just don't know how to use Twinview properly.  Can you use Twinview as a single desktop across two screens?

Teejeaux

---

### Post by SEMW on 2008-05-16
> **RAOF said:**
> That is a hardware limit; there are (moderately evil) ways of working around it, but none are being actively developed as far as I know.

How does Vista get around this, if it's a hardware limit?

(More info: I have an ATi card with a max_texture_size of 2048; and sure enough, running compiz with dual screens side-by-side quits with a max_texture_size error; forcing compiz to run with SKIP_CHECKS=yes results in garbage for pixel columns 2049 through 2832.  But the Aero Glass compositor works fine with dual monitors).

---

### Post by RAOF on 2008-05-16
> **SEMW said:**
> How does Vista get around this, if it's a hardware limit?

(More info: I have an ATi card with a max_texture_size of 2048; and sure enough, running compiz with dual screens side-by-side quits with a max_texture_size error; forcing compiz to run with SKIP_CHECKS=yes results in garbage for pixel columns 2049 through 2832.  But the Aero Glass compositor works fine with dual monitors).

Obviously, I'm not intimately familiar with the Windows compositor ;).  My guess would be, however, that (1) Either they use the slightly-crazy-hack, where you split a big window into multiple textures, or (2) they don't allow really big windows :).  The reason why you see craziness in Ubuntu is that the root (or desktop) window is the full width and height of the combined monitors; if Windows didn't do this, and had separate desktop windows for each head, the hardware limitation would be much less noticable.

> **teejeaux said:**
> But Twinview creates two completely different desktops, not a single desktop that covers both screens, correct? I don't want two different desktops. I use the two screens as a single screen, passing things back and forth, and sometimes I use them as a single screen and spread a window all the way across it.  Or maybe I just don't know how to use Twinview properly.  Can you use Twinview as a single desktop across two screens?

Teejeaux

No.  TwinView gives you a single desktop spanning both screens.  And, as long as both monitors are connected when you start X, maximising and stuff will work as you'd expect (ie: a window will maximise to fill one screen, not both).

---

### Post by teejeaux on 2008-05-16
> **RAOF said:**
> 
No.  TwinView gives you a single desktop spanning both screens.  And, as long as both monitors are connected when you start X, maximising and stuff will work as you'd expect (ie: a window will maximise to fill one screen, not both).

Thanks for the help RAOF!  I seem to have gotten Twinview working, and most of what it's supposed to do is working properly, but for some reason it won't let me create multiple desktops/workspaces.  Any suggestions? 

Thanks,
Teejeaux

---

