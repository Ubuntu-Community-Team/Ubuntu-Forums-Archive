---
title: "Screen shuts off when visiting certain websites"
date: 2014-11-11
forum: General Help
---

### Post by hans-nesse-6 on 2014-11-11
I have rather a puzzle.  When I visit certain websites in certain browsers, my computer will freeze and not accept inputs for a few seconds, and then the screen goes dark.  I can reliably reproduce this when I visit the chrome website ([www.google.com/chrome](www.google.com/chrome)) in Firefox, but I have observed this as well in the chrome browser visiting youtube (always at the start of a new video).  Once the screen is dark, I have to force a restart.  

When the screen goes dark, if a video is playing the audio continues, but keyboard commands (eg volume) no longer work.  The hard drive LED continues to flash, as does the network LED.  

I'm rather at a loss as to how a website could force hibernation or something similarly low level.  I've checked the CPU temperature with sensors and it is pretty normal (well below critical).  I've looked at logs, but honestly I don't know most of what I am looking at or what to look for.  I uninstalled flash plugin, and reinstalled firefox, but neither seemed to fix it.

I am running ubuntu 14.04 on a Dell 1525.  

Any thoughts or suggestions would be appreciated. I am rather at a loss.

---

### Post by Yulra on 2014-11-11
I had a similar problem appeared to be the graphics card for me. Is it just flash websites (e.g youtube?)

When you say force a restart... have you tried Ctrl + Alt + F1, to drop back to a none GUI shell? I found that only Alt + SysRq + SUB works for restarting the system safely at that point. (However I must point out that REI and K don't work in Ubuntu 14.10... not sure if this is true for earlier versions)

---

### Post by hans-nesse-6 on 2014-11-11
Thanks for the reply.  I could only get it to restart by holding the power button (I have tried both other methods).  I also tried disabling the addons in firefox.

I assume that there's something with graphics intensive websites which is triggering this, I don't know if it is flash or not (I uninstalled the flash plugin and have not yet reinstalled it, but the problem persists).  You may be right that this is a graphics card issue, but I am not sure how to diagnose it (I did use system testing, and passed).

---

### Post by Yulra on 2014-11-11
Which graphics card do you have? Mine appears to be more related to xorg than anything else. >.>

---

### Post by hans-nesse-6 on 2014-11-11
It comes up as Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])

---

### Post by hans-nesse-6 on 2014-11-11
Okay, I have updated my Intel graphics card driver and it seems to have fixed the problem... ish.  I have not been able to get a black screen since updating the driver, however chrome now causes unity launcher to crash--no launcher, no button to close windows, etc.  Fortunately, I can open the command line and shut down properly, but still a bug of some sort.  I have not run into any problems in firefox as of yet.

---

