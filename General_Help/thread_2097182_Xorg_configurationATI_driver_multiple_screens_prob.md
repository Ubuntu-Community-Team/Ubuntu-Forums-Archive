---
title: "Xorg configuration/ATI driver multiple screens problem"
date: 2012-12-22
forum: General Help
---

### Post by ThePossessedOne on 2012-12-22
Hello guys!

Not strictly a ubuntu problem but Mint is similar to Ubuntu and I've tried over in their forums and the support isn't as good as Ubuntu's community.

Anyway I'm having an annoying Xorg problem...

I'm  running a ATI HD Radeon 6870, Linux Mint 14 Nadia 64 bit MATE freshly  installed and installed the 'stable' ATI driver from their website (the  .run file)

I have tried to run
[INDENT]> 1. When the message about viewing the X server output came, I pressed Ctrl Alt F2
2. Now on the new shell I ran command sudo Xorg -configure
3. Then I copied /home/oobe/xorg.conf.new to /etc/X11/xorg.conf
sudo cp /home/oobe/xorg.conf.new /etc/X11/xorg.conf
4. At last I started X using command startx[/INDENT]Which  fixed the same issue of 'no screens found' on my little netbook  (running Mint 13 32bit) but the computer I am having a problem on has 3  monitors;

Monitor 0 - 1920 x 1080
Monitor 1 - 1920 x 1200
Monitor 2 - 1920 x 1080

These  ran fine which the default driver that came with a fresh install of  Nadia 14 64bit and I could drag windows between screens etc. But  obviously this wasn't utilizing the power of the graphics card so I  installed the ATI driver and ran into the Xorg problem then ran the  commands in the quote above but I'm guessing this doesn't work in 14 due  to some changes or the fact I'm trying to setup 3 monitors? 

> (-- log file: "var/log/Xorg.0.log", Time Sat Dec 22 00:59:06 2012
(==) Using config file "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Initizializing ...

Then:

Loading GLX
(II) [KMS] drm report modesetting isn't reported.
vesa: ignoringin device with a bound kernel driver
(II) [KMS] drm report modesetting isn't reported.
vesa: ignoringin device with a bound kernel driver

Fatal server error: 
no screeens found 
(EE)When I enter sudo Xorg -configure I get:

> using config file: "/home/Tom/xorg.conf.new"
using system config directory "/usr/shre/X11/xorg/conf.d"
Drm report modesetting isn't supported/
vesa: Ignoring device with bound kernel driver

Backtrace:
0: Xorg (xorg)backtrace+0x36) [0x7f47414f9ac6]
1: Xorg (0x7f4741351000+1ac8f9)  [0x7f47414fd8f9] 
2: /lib/x86_64-linux-gnu/libptthread.so.0 ...


Segmentation fault at address 0x0

Fatal server error:
Caught signal 11 (segmentation fault. Server aborting
Any help is appreciated!

---

### Post by ThePossessedOne on 2012-12-22
bump

---

### Post by ThePossessedOne on 2012-12-22
Bump

---

### Post by ThePossessedOne on 2012-12-23
bump

---

### Post by ThePossessedOne on 2012-12-27
EPIC bump

---

