---
title: "Freezes that I can't seem to recover from"
date: 2008-05-07
forum: General Help
---

### Post by inzania on 2008-05-07
Hey all - every so often, Ubuntu 8.04 seems to lock up, graphically and otherwise, except that the mouse is still responsive.  I am unable to click on anything or otherwise interact at all.  The most common thing that seems to trigger this is double clicking any file that opens in the default movie player (which are standard .avi or similar files).  When the freeze occurs, I try Ctl+Alt+Backspace, Ctl+Alt+Del, and finally even Ctl+Alt+Sysreq+R followed by Ctl+Alt+Del.  The last (sysreq) produces a system beep and _sometimes_ succeeds in rebooting the machine, but not always.

I'm not sure what other information to give, but this is a really annoying crash bug.  Anything that might fix it would be much appreciated.

---

### Post by wootah on 2008-05-07
Are you able to switch to a terminal (CTRL-ALT-F1 or F2, etc)? You could try and do a top to see if something is eating cycles. You may be able to recover that way or further diagnose what is happening.

If you have a SSH server up, you could try logging in that way too.

---

### Post by SureStandar on 2008-08-30
hi, i have the same problem. whole system freezes when opening an .avi file. not always though. no response from anything (haven't tried raising skinny elephants yet). is it something that can be fixed?
thanks :guitar:

---

### Post by tomsen_san on 2008-09-23
I have the same symptoms as described at the top and I did as wootah suggested (after lockup connecting using ssh from a remote box) and found that process Xorg is eating the CPU to 100%. I tried kill -9 which did not work but could at least reboot the system. 
I have a vanilla Ubuntu 8.04 install, latest updates, open source Ati-driver, nForce2 board with an Athlon 2600+ and Ati X800GT AGP.
Yorg seems stuck in endless loop. I can create the problem by typing some more in OpenOffice or Thunderbird.

---

