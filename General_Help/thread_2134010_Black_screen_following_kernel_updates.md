---
title: "Black screen following kernel updates"
date: 2013-04-09
forum: General Help
---

### Post by memilanuk on 2013-04-09
So... I've got a Lenovo ThinkPad T530 that has been dual-booting Linux and Windows 7  Pro for a few months now.  Primarily using Ubuntu 12.10 w/ no problems.   Had some weirdness on Fedora 18 and Fuduntu 2013.1 where it ran the  live usb just fine, installed just fine, but then after updates wouldn't  display anything after grub2 other than an unresponsive black screen.  I  went back to Ubuntu 12.10 because it seemed to work without any  problems.

 
Now today I downloaded and installed the latest  kernel updates... 3.5.0-27generic, and rebooted.  Same blasted thing -  nothing but a black screen, and the only thing it responds to is  Ctrl+Alt+Del to reboot, or holding down the hardware power switch until it turns  off.

 
At this point I'm pretty comfortable that this is  *not* a distro-specific issue, but something between a newer kernel  (which both Fedora 18 & Fuduntu 2013.1 w/ updates would have gotten  as well) and the ThinkPad hardware.  The question is 'what?' and how to  get it sorted out.  I'm able to select the previous kernel  (3.5.0-26generic) from the 'Advanced Ubuntu options' @ grub2, and that  boots as expected.  Booting the 3.5.0-27failsafe option at least shows  the startup messages, but seems to lock up partways thru.  Any help on  what to do next would be much appreciated.

Monte

---

