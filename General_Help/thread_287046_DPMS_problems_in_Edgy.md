---
title: "DPMS problems in Edgy"
date: 2006-10-28
forum: General Help
---

### Post by jdunn on 2006-10-28
Please help me out!!  In Dapper, I could edit the xorg.conf file to get DPMS running so my display would power-off after 30 minutes of inactivity. Now, I'm using a fresh install of Edgy and I can't get DPMS to work. I'm not sure if the new xorg, new nvidia drivers or linux kernel is the problem. I've tried enabling DPMS in System Settings>Monitor&Display too (I'm using Kubuntu).

I'm using a Gforce 5600 with the 8774 glx drivers.

I also tried 'xset dpms 300 600 900' and it only blanks the screen with a large 'X'...It doesn't change the display power mode. 

XSET -Q OUTPUT
--------------------------------
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  250    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  20/10    threshold:  2
Screen Saver:
  prefer blanking:  no    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 300    Suspend: 600    Off: 900
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log
--------------------------------

I also tried 'xset' on the LIVE Edgy CD and the display did turn off.  This leads me to believe my problem has something to do with the Nvidia driver.  I have found nothing about this in the Nvidia forums.

---

### Post by jdunn on 2006-10-28
*Bump*
I uninstalled the Nvidia drivers, disabled Hyperthreading in the kernel, and disabled NTP (which I was using to keep my clock in sync)...assuming any one of these might cause DPMS not to work.  It made no difference.  I can't really think of what else I should disable, other than doing a complete reinstall of Kubuntu from scratch.  I have some opengl games on here, Build-Essentials, Gimp, Blender and their dependancies...that's about all I have on top of the basic Kubuntu 6.10 install.

I'm assuming DPMS would have worked for a short time if I'd enabled it immediately after the Kubuntu install...because when I ran Kubuntu 6.10 from the Live CD, I made DPMS work with 'xset'.

As usual, no one from these forums can offer any suggestions.

---

### Post by jdunn on 2006-10-28
*bump*

---

### Post by vibestriton on 2006-10-28
You say it works from the LiveCD?  Have you compared the xorg.conf file there to the one on your current install?

Just a thought.

Have you tried doing the 'diff' thing on related files between the LiveCD/current install?

---

### Post by jdunn on 2006-10-29
> **vibestriton said:**
> You say it works from the LiveCD?  Have you compared the xorg.conf file there to the one on your current install?

Just a thought.

Have you tried doing the 'diff' thing on related files between the LiveCD/current install?

I was about to diff the two files as you suggested but I decided to try adding "Option" "DPMS" to my xorg.conf again.  This time, it worked (maybe I did something wrong earlier or maybe reinstalling the nvidia drivers helped).  On my linux install, I can set DPMS Standby/Suspend/Off times with xset.  However, I still can't set DPMS Standby/Suspend/Off times with KDE.  Any changes I make in 'System Settings->Monitor&Display->Power Saving' reverts to 5 hours.

---

### Post by padre999 on 2006-12-07
In KDE it is a bug...

[http://kubuntuforums.net/forums/index.php?topic=10439.0](http://kubuntuforums.net/forums/index.php?topic=10439.0)

---

