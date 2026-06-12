---
title: "Feisty freezing, possibly because of wireless problems?"
date: 2007-08-04
forum: General Help
---

### Post by GreatestGravity on 2007-08-04
Hey all,

So, as of this morning, I had issues with Feisty freezing. It happened like this:

First the wireless connectivity flickers and shuts off.
Then (0-10 seconds later), all of the lights on the keyboard start flashing, and the keyboard stops responding.
The mouse also stops responding, though there was one instance when it didn't.

If I disable my wireless card, this doesn't seem to happen, though it's hard to tell because it's random anyway. 

The thing that happened this morning that might have triggered it was me installing some updates the update-manager suggested - from Synaptic's history, I see

Commit Log for Sat Aug  4 10:11:34 2007

Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libdbus-1-dev (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
python-launchpad-bugs (0.1.13) to 0.1.13.2
tzdata (2007e-0ubuntu0.7.04) to 2007f-0ubuntu0.7.4

It seems like one of those is probably the issue since I made the upgrade right before it started happening, but it's hard to tell, could be a false lead...

Does anybody have any idea what my problem is or what I can do to fix it? I'm running a dell inspiron 600m laptop, with a broadcom wireless card. Is there any other relevant information I should provide? I've tried searching the forums, but haven't found anything that looks like it could be a description of my problem or a fix for it, I'm not sure what to look for besides "freeze". 

...okay, so now that it's the late evening, the problem seems to have gone away - maybe the internet connectivity got better. Still, if anyone has any idea why disrupted wireless would cause freezes, I'd appreciate it, since I'd like to figure out how to make sure the issue doesn't come up in the future. I guess since I can't duplicate it right now it'll be hard to diagnose, but maybe someone else has had this solved already and can point me somewhere.

---

### Post by GreatestGravity on 2007-08-05
...and now I'm having issues with X. I'm guessing it's related, because my system's been running fine for a long while, and now there's a couple of things at once.

I've had XMMS die on me, with the error message 

Gdk-ERROR **: X connection to :0.0 broken (explicit kill or server shutdown).  

and have had Firefox die on me, with the error

The application 'Gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Segmentation fault (core dumped)

Any hints as to where to look now? Both of those errors come after a while of use, and without any sort of prompting, as far as I can tell.

---

### Post by GreatestGravity on 2007-08-05
Please, somebody, point me somewhere... in a moment of wireless iffiness, my laptop becomes totally unusable. When I'm on a virtual terminal at the time of the freeze, I see kernel panic. Right now the internet doesn't seem to be flickery and so I can actually type, but it's so on and off. I don't know what to do besides renounce internet - I don't know where to even start looking right now, I've looked everywhere I can and tried some things without any luck.

---

### Post by glepore70 on 2007-08-05
I also had wireless problems after updating today.  I had been away so there were several days worth of updates, so I cannot narrow it down too much.  My network froze while installing the updates (via apt-get).  At the same time I was vnc'ing to another computer.  Apt froze up and when I rebooted my wireless network was gone.  I fiddled around for three or four hours and it eventually came back, but I cannot tell exactly what I did.  Although it seemed that network manager was having a hard time remembering the WEP key for the access point...

---

### Post by GreatestGravity on 2007-08-05
Okay, so maybe I'm getting somewhere now. In a fit of wireless connectivity (trying not to jinx it...) I've had time to look through random logs and things, and right before the crash, /var/log/kernel.log shows pages and pages of 

"Open Authentication completed with 00:09:5b:a1:86:6f"

interspersed with 

"printk: X messages suppressed." 

where X is somewhere between 1 and 13 right before the crash.

wireless card info, since it might be relevant: "Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)", using the native Feisty drivers. 

Maybe I'm getting somewhere...

I'm also reading through this thread ( [http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)  ), seeing whether any of the people there have potential solutions. I've tried the one that deals with the network-manager - enable the other interface, and give the location a name... have put in some of those kernel options suggested, especially as I do get a "try pci=assign-busses" somewhere in kernel messages.

Right now it's back to being stable, but that's likely because the wireless connectivity is better rather than because of anything I've done. I guess I'll find out sometime later whether any of the things I tried actually helped.

I think that disabling the wireless in BIOS makes the problem go away, but that doesn't help since I want my internet!

---

### Post by izizzle on 2007-08-16
The problem is the python update that was installed, disable the python process and see if it crashes.

best of luck- izizzle

---

