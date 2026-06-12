---
title: "kino problems! (not recognizing camera)"
date: 2005-05-13
forum: General Help
---

### Post by daryl314 on 2005-05-13
I've been trying to get kino to work on ubuntu, but haven't had any luck.  I followed the instructions in the wiki ([http://www.ubuntulinux.org/wiki/HowToCaptureDigitalVideo)](http://www.ubuntulinux.org/wiki/HowToCaptureDigitalVideo)), but that didn't seem to work.  When I fire up kino and go to the capture screen, I get the error "No AV/C compliant cam connected or not switched on?".  I know that the camera works because I am able to reboot into Windows XP and capture the video.  Any suggestions for getting this to work?

---

### Post by tomp88 on 2005-05-13
Had this problem many times.   Make sure you fire up kino as root.
You can prolly set it up later for non-root use.
Good luck!

---

### Post by daryl314 on 2005-05-13
[QUOTE=tomp88]Had this problem many times.   Make sure you fire up kino as root.
You can prolly set it up later for non-root use.
Good luck![/QUOTE]

running as root fixed an earlier problem i was having where kino was complaining about access to /dev/raw1394.  unfortunately the problem i'm describing popped up after i fixed the root issue.

---

### Post by daryl314 on 2005-05-14
according to the folks at kino, the 2.6 kernel is flakey with firewire stuff before 2.6.12.  i might just have to wait for ubuntu to come out with a more updated kernel.

---

### Post by tomp88 on 2005-05-14
Oops, forgot about that.  I believe this is why Mepis provides a choice of 2.4 or 2.6 kernels on boot.  You could do the same with Ubuntu by adding a stanza to your boot loader.  Then you could use 2.4.x when you want to play with 1394.  This would get you up and going without waiting for a newer 2.6.

Worth a try?

Regards

---

