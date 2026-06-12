---
title: "can't disable screen saver"
date: 2007-11-24
forum: General Help
---

### Post by seasom on 2007-11-24
this is driving me nuts...

using a fresh install of gutsy 7.10 with compiz

I have the screensaver set to "Regard computer as idle after 2 hours" and i unchecked "activate screensaver when computer is idle".

under power management, AC power is set to put the comptuer to sleep never, go blank screen when laptop lid is closed, put display to sleep when inactive for never.  same exact settings for on battery power.

within about 5 minutes of not touching the mouse the screen goes black.

what'd i miss?

---

### Post by specialk4urmind on 2007-11-28
im having the same problem.  I have a fresh 7.10 on my laptop and dual booting with XP.  I have power management set so that it'll never turn off anything if ac adapter is plugged in.   In screensaver, I have regard computer as idle in 3omin but the option for "active screen saver when computer" is not flagged.  Also in power management I have put display to sleep when in active on never!  Why is it turning the screen off?  I'm very new to linux/ubuntu.  I can't watch my dvds cuz the screen turns off.

---

### Post by Sarteck on 2007-11-28
I'm having much the same problem, here.  Every ten minutes I have to move my mouse or hit some key to turn off the screensaver, which is really annoying when I am trying to watch movies on Kaffeine, or play my video games on pSX (I use a USB controller instead of the keyboard, so I guess pressing buttons isn't recognized for stopping the screensaver).

At first I thought it was Compiz-Fusion that was causing the problem, so I uninstalled it (it's nice, but not something I really need), because I didn't start experiencing the problem until I installed Compiz-Fusion.  Unfortunately, it didn't solve the problem....

---

### Post by jcarlock on 2007-11-30
Again Confirmed...  Gutsy 7.10 w/Compiz

1.8 GHz Celleron
1 GB DDR
ATI X800 Pro 256 MB


I feel like it might be the ati AMD driver. 8.42 I think, newest as of Dec07.

---

### Post by Sarteck on 2007-11-30
Using an nVidia GeForce 6150 here...```
sarteck@auron:~/Desktop/rt61-cvs-2007113010/Module$ lspci | grep GeForce
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
```Funny, it really -is- a 6150, even though it says 6100...

---

### Post by Maddmaxx on 2007-12-02
Same problem here, everything disabled in the screensaver control, and I have to keep moving the mouse while watching movies. Screen goes blank after 5 minutes and 5 more minutes later the screen shuts off, I'm led to believe that I am somehow running 2 screensaver daemons, but can't find a second one, this is really annoying, and through dozens of searches and endless reading and expirimentation, I can not shut off the screensaver...PLEASE HELP US!!!

Gutsy 7.10
Latest ATI Drivers (9800 Pro)
Compiz

---

### Post by theheadlessrabbit on 2007-12-05
I'm having the exact same problem on my Fujitsu lifebook a series.


screensaver is set to '2 hours' Everything else is set to 'never', but after 10 minutes, the screen goes blank, anyway.

this is really annoying.  

I'm an artist, and after i create my images in the gimp (which doesn't suck any more - thank you!) I paint from the screen.   when it goes black, i have to reach over and hit a button- and i get paint all over my lappy. 

 this is not good.


please don't make me go back to using XP to do my work.

ATI radeon graphics, AMD sempron processor.
dual boot ubuntu / winXP.

---

### Post by pinguy on 2007-12-06
Same here. I have a ATI Xpress 200 running gutsy 7.10 with compiz on a Compaq desktop  PC.

This really needs to get sorted, it makes watching videos a nightmare.

---

### Post by Saint Angeles on 2007-12-06
same here...

and also, sometimes when i'm zoomed in on a movie or something, the mouse cursor will move to the right a good 200 pixels or so.

the latest compiz hasnt been good to me

---

### Post by rileyrg on 2007-12-06
Same on Debian Testing FWIW.

---

### Post by spamgoat on 2007-12-12
I have the exact same. Any known solution yet?

Edit: A solution is offered [here]("http://ubuntuforums.org/archive/index.php/t-442190.html"). I've yet to try it myself.

---

### Post by ugm6hr on 2007-12-15
The issue of being unable to watch videos is a major problem.  I have an ATI 1100 graphics card on my Acer 5051 laptop with Ubuntu7.10.

Having tried (and failed) to disable the screen power-saving feature, I was wondering if anyone else has succeeded.

Not that I like comparing Windows with Ubuntu, but I believe that some video playing software in Windows actually temporarily overrides the screensaver setting to allow you to watch videos uninterrupted, but maintains the screen protection at other times.  Is this a possibility for a future Ubuntu (or Totem etc)?

The solution linked ([http://ubuntuforums.org/showpost.php?p=2651344&postcount=6](http://ubuntuforums.org/showpost.php?p=2651344&postcount=6)) might resolve this for me - but it does mean I will never have a functioning screensaver.

---

### Post by herorev on 2007-12-24
I'm having this problem on Kubuntu 7.10 (upgraded from 7.04). I have an Nvidia graphics card and I'm not running Compiz (just KWin).

Has nobody discovered the cause of this problem? I found a bug for it here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575)
But there doesn't seem to be any progress on it.

---

