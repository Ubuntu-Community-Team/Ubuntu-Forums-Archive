---
title: "Switching user hides mouse pointer"
date: 2016-06-05
forum: General Help
---

### Post by pfeiffep on 2016-06-05
I was testing the capability of adding a new user to this laptop and found the mouse pointer disappeared.
This is a *minor annoyance*  ...........Here's the sequence:
```
added a normal desktop account
used switch user option on logout button
logged into new user account
changed background, launched ThunderBird, added logout button to top panel
switched user again
logged back in as myselt - no mouse pointer was available
Ctrl-Alt_tto launch terminal and entered sudo init 6 to reboot
```

Machine specs
```
CPU~Dual core Intel Core i3 M 330 (-HT-MCP-)
 speed/max~933/2133 MHz 
Kernel~4.4.0-22-generic x86_64 
Up~35 min 
Mem~1207.7/7654.6MB HDD~500.1GB(5.1% used) 
Procs~199 
Client~Shell inxi~2.2.35
Graphics:  Card: Intel Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1600x900@60.21hz
           GLX Renderer: Mesa DRI Intel Ironlake Mobile
           GLX Version: 2.1 Mesa 11.2.0
```

I'm not certain exactly for what to search syslog

---

### Post by jeremy31 on 2016-06-05
Does this [work around](http://ubuntuforums.org/showthread.php?t=2321311&p=13474801&viewfull=1#post13474801) work for you?

---

### Post by pfeiffep on 2016-06-05
Thank You! @jeremy31 
I use this so** infrequently** that a simple raise terminal and enter _**ls -al**_ returns the mouse pointer

Of course I could simply log out vs switch user.  There's a bug already reported in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604")

---

