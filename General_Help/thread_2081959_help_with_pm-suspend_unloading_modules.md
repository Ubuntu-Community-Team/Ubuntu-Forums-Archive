---
title: "help with pm-suspend unloading modules"
date: 2012-11-08
forum: General Help
---

### Post by jonnybignote on 2012-11-08
Hello all

in the continuing struggle to get suspend and resume back on my desktop machine running 12.04 64bit, can anyone give any advice on unloading of modules?

I currently experience crashes/freeze with while going into standby or trying to resume.  Every 10th try or so, it seems to work ok, but there is no patter I can discern.

I can't find anything quite like my issues online, and I don't see an epidemic related to 12.04,  so I figured it might be some kind of kernel incompatability with my hardware so I'd go to work at trying to selectively unload kernel modules or hardware prior to suspending, until I get a working suspend.

I've previously been able to do this with things like my tv tuners, but I don't have any experience with anything deeper than that, so any help would be greatly appreciated.  I have had this hardware working perfectly and suspending correctly in previous versions of Ubuntu/Mythbuntu.

Thanks!

Gigabyte MA74GM-S2 with NVIDIA 8600

---

### Post by hal8000 on 2012-11-08
Have you looked through /var/log/messages to see if there any clues as to the problem?

If you dont get a display may be worth perusing /var/log/Xorg.0.log as well.

---

### Post by jonnybignote on 2012-11-08
Thanks hal8000 for the reply.

I had been looking at the logs and nothing jumped out at me.  

I did however just have the idea of pulling out all remaining usb devices (only two still connected are my wireless kb/mous reciever and my remote reciever (I have ssh access from another machine).

I've been able to trigger seven or so pm-suspend resume cycles in a row!

Unbelievable - I should have done that 3 days ago, but they have never been an issue all the way from 9.04 through this one, so it never occurred to me.  

I'll now trace which one exactly is the culprit, then I'll google around to see how to unload it before suspending

The question now is - after being unloaded, will that device now be unable to wake up the computer??  kind of a deal breaker if its the remote receiver...

Thanks again for the help

---

### Post by jonnybignote on 2012-11-08
I can't seem to suspend with either plugged in - maybe it is an incompatibility with my motherboard and the kernel handling of USB.

I tried plugging in just a webcam and that also made it freeze up, so I guess that is the issue - any usb device is going to cause problems - something to do with the handling of USB power or the hub....not sure.

I'm transitioning this machine to backend only, so I can control it with ssh and vnc, but it will be strange to not have any other connection to it - and I don't know how tolerant bios's are these days to now having keyboard/mouse attached...

Any thoughts on handling the usb ports appreciated.

---

