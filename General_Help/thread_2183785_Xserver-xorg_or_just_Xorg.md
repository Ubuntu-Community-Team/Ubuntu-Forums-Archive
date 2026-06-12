---
title: "Xserver-xorg or just Xorg?"
date: 2013-10-26
forum: General Help
---

### Post by ibjsb4 on 2013-10-26
I am running without a display manager (using startx) and xorg package installed, works fine.

I also run a virtual machine (a pretty bare install) using just the package  xserver-xorg.  Which also seems to work fine.

So the question is:
Can I use just the package xserver-xorg in the real world (desktop installed) or will I miss the extra packages that comes with the xorg package?

If you wonder why I want to do this, its just part of the never ending quest for minimal everything :D

EDIT: I guess I should mention that I run metacity only, no compiz installed.

---

### Post by TheFu on 2013-10-27
You need a minimal window manager.  I'm like you - I run fvwm as my WM.  No need to worry about which X packages are pulled in, the dependencies will handle that for you.

Take a look at the starts script - educational, it is.

---

### Post by tgalati4 on 2013-10-27
*xserver-xorg* has a huge list of dependencies.  Without repackaging, I don't see how you could reduce them.  If you want minimal X-Windows, look at [http://tinycorelinux.net/welcome.html](http://tinycorelinux.net/welcome.html) and how they handle a minimal X-server.

tgalati4@Mint14-Extensa ~ $ apt-cache depends xserver-xorg
xserver-xorg
  Depends: xserver-xorg-core
 |Depends: xserver-xorg-video-all
  Depends: <xorg-driver-video>
    fglrx
    fglrx-updates
    nvidia-173
    nvidia-173-updates
    nvidia-current
    nvidia-current-updates
    nvidia-experimental-304
    nvidia-experimental-310
    virtualbox-guest-x11
    xserver-xorg-video-ati
    xserver-xorg-video-cirrus
    xserver-xorg-video-dummy
    xserver-xorg-video-fbdev
    xserver-xorg-video-intel
    xserver-xorg-video-mach64
    xserver-xorg-video-mga
    xserver-xorg-video-modesetting
    xserver-xorg-video-neomagic
    xserver-xorg-video-nouveau
    xserver-xorg-video-openchrome
    xserver-xorg-video-qxl
    xserver-xorg-video-r128
    xserver-xorg-video-radeon
    xserver-xorg-video-s3
    xserver-xorg-video-savage
    xserver-xorg-video-siliconmotion
    xserver-xorg-video-sis
    xserver-xorg-video-sisusb
    xserver-xorg-video-tdfx
    xserver-xorg-video-trident
    xserver-xorg-video-vesa
    xserver-xorg-video-vmware
 |Depends: xserver-xorg-input-all
  Depends: <xorg-driver-input>
    xserver-xorg-input-acecad
    xserver-xorg-input-aiptek
    xserver-xorg-input-elographics
    xserver-xorg-input-evdev
    xserver-xorg-input-joystick
    xserver-xorg-input-kbd
    xserver-xorg-input-mouse
    xserver-xorg-input-mtrack
    xserver-xorg-input-multitouch
    xserver-xorg-input-mutouch
    xserver-xorg-input-penmount
    xserver-xorg-input-synaptics
    xserver-xorg-input-tslib
    xserver-xorg-input-vmmouse
    xserver-xorg-input-void
    xserver-xorg-input-wacom
  Depends: xserver-xorg-input-evdev
  Depends: libc6
  Depends: xkb-data
  Depends: x11-xkb-utils
  Recommends: libgl1-mesa-dri
  Conflicts: xserver-xorg:i386

---

### Post by TheFu on 2013-10-28
+1 on TinyCore.  I'm with @tgalati4.  Use it all the time for my online banking and brokerage access VM.  12MB for a working OS with a GUI. They have 3 versions:
* no GUI - about 4M
* minimal GUI w/browser - 12M
* GUI w/popular browser and common tools - 64M

Definitely good for a quick need, but lacking in infrastructure software things that even I want on a daily use machine.  OTOH, TinyCore is FAST on any machine - don't think we could tell the difference in speed between a Pentium4 and a Core i7. ;)

I know that IBM started with TinyCore as the base for a remote computing desktop project for about 10K people too. Can't recall if they used NX, Spice, VNC, RDP or something else as the main protocol.

---

### Post by ibjsb4 on 2013-10-28
Yes, I will have to research how tinycore builds X.  I realize that I am basically just reinventing the wheel, but this is something I like to do :)

The little bit of research I have done on this, indicates that I could just install xserver-xorg-core and build up from there.

I haven't look at those start scripts yet, home work is piling up :)

This is going to take a few weeks, depending on how many times this little project gets shove off to the back burner.  So expect another post in a few weeks.

Thank you both :)

---

### Post by VMC on 2013-10-28
CorePlus 5.0 is 74+ megs now. I never thought of using in a VM. I think I will try it. 
Installing apps is a bit odd compared to apt-get, but its small size and speed make up the difference.

---

