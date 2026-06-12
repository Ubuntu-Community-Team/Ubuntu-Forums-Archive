---
title: "Hardy freezes when inactive"
date: 2008-05-15
forum: General Help
---

### Post by Poilar on 2008-05-15
I'm not having the problems that some people are having of totally random freezes. Hardy seems to only freeze for me when inactive. If I don't touch my computer for a while then it tends to freeze. It doesn't always freeze, but if the computer is inactive for long enough than it usually does. The screen is typically black at this point (screen saver) and there's nothing I can do other than hard reboot. Even the REISUB alternative doesn't work.

Also, there are no errors being shown in any of my logs that I can see.

Ideas?

I'm running a Thinkpad T60 with all Intel components (wireless card, graphics card, and whatnot) and had no freezing problems with any earlier version of Ubuntu.

---

### Post by jimv on 2008-05-15
When you say freeze, do you mean that the screen is black and won't come back up?

---

### Post by Poilar on 2008-05-15
> **jimv said:**
> When you say freeze, do you mean that the screen is black and won't come back up?

Exactly. The screen is black like the screensaver is on, but I move the mouse and nothing happens. Can't switch to another terminal. Can't ctl-alt-delete. Can't use REISUB. The only thing I can do is hold down the power button for a few seconds to hard boot.

Actually, oddly enough, once I had sound playing when it froze and, though the sound immediately got all garbled in that frozen on one note sort of way, the mute button still worked so I could turn off the sound.

---

### Post by jimv on 2008-05-15
My laptop was doing something similar...if I let it sit for too long, it wouldn't come back from the blanked screen...though control+alt+delete usually fixed it.

I finally worked around it by disabling screen blanking in the power saving settings and in my xorg.conf.  Here's the changes I made to my xorg.conf:

```
Section "ServerFlags"
	Option	"BlankTime"	"0"
	Option	"StandbyTime"	"0"
	Option	"SuspendTime"	"0"
	Option	"OffTime"	"0"
EndSection
```

---

### Post by muanis on 2008-09-24
I'm having the same problem, did disabled the same stuff on xorg and it keeps freezing.

HP6515b
Hardy last updates until today with fglrx driver

---

### Post by Poilar on 2008-09-24
My freezes have stopped and, while I'm not 100% certain, there seemed to be a correlation to my switching to use the e1000e module as opposed to the e1000 module. I found the following text somewhere online relating to OpenSuse:

"Here a short description how to fix the 82573L network chip problem on
OpenSuse 10.3. The Intel Pro/1000 82573L chip is used on various notebooks
(Lenovo Thinkpad T60, X60, HP, Samsung Fujitsu Siemens,...). OpenSuse 10.3
uses the e1000 module for this chip and especialy when in gigabit mode,
various problems can appear (ping latency, complete system crashes, extremly slow network performance and delays). Various methods are described on the net trying to fix the problem (RxIntDelay,...), however, none really worked 100% on my T60 wich showed basicly all described problems incl. complete kernel crashes."

Those symptoms were the same that I was having. I also read somewhere about how the e1000e module was newer and should technically be used anyway. However, the e1000e module shipping with Ubuntu is non-functional (i.e. your ethernet just won't work). So, I downloaded the e1000e module from its website ([http://sourceforge.net/project/downloading.php?group_id=42302&use_mirror=superb-east&filename=e1000e-0.4.1.7.tar.gz&97058153](http://sourceforge.net/project/downloading.php?group_id=42302&use_mirror=superb-east&filename=e1000e-0.4.1.7.tar.gz&97058153)), compiled it, and copied it to /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000e/e1000e.[k]o (copying over the version currently there).

Then I blacklisted the e1000 module in /etc/modprobe.d/blacklist and I whitelisted the e1000e module in /etc/modules

I reloaded the boot list via sudo update-initramfs -u

And voila! No more freezes! You should be aware that every time Ubuntu has a kernel update the e1000e module is overwritten so you have to recopy the compiled version of e1000e to the location above.

---

### Post by gillza on 2009-07-09
> **jimv said:**
> My laptop was doing something similar...if I let it sit for too long, it wouldn't come back from the blanked screen...though control+alt+delete usually fixed it.

I finally worked around it by disabling screen blanking in the power saving settings and in my xorg.conf.  Here's the changes I made to my xorg.conf:

```
Section "ServerFlags"
	Option	"BlankTime"	"0"
	Option	"StandbyTime"	"0"
	Option	"SuspendTime"	"0"
	Option	"OffTime"	"0"
EndSection
```

I don't want to jinx it but this seems to have helped me so far. I am using Xubuntu 9.04 and it was randomly freezing when inactive. It actually froze even when I was testing the live CD...

---

