---
title: "Ubuntu 16.04 boots into emergency mode when fstab entry not really present"
date: 2016-08-23
forum: General Help
---

### Post by Martin_Kellner on 2016-08-23
I have a USB drive at work that's specified in fstab (although the pathname says RAID it's not an array, just a single USB drive of 2 Tb). In 14.04, when I booted the computer without the drive connected, I would get an option during boot to skip that and then it would boot just fine. In 16.04 however, it boots into emergency mode instead. I can get around this by booting in startup mode but it's really annoying. How can I get around this? My fstab entry for the drive looks like this:
```
#USB drive
UUID=1ade5a24-10bf-4010-aa99-75fb16d4ce32    /home/user_id/RAID    ext4    rw,user    0    0
```

---

### Post by QLee on 2016-08-23
For an external drive that is not always connected you may want to use the "noauto" option in fstab (don't try to automount), the fourth field in the fstab line. More info about the options and fstab mounting by entering, man fstab, in a terminal window to read the manual.

---

### Post by Martin_Kellner on 2016-08-23
Thanks, I will try that

---

### Post by steeldriver on 2016-08-23
There used to be a nobootwait option for exactly this situation - but it seems to have been removed

[http://askubuntu.com/questions/786928/ubuntu-16-04-fstab-fails-with-nobootwait](http://askubuntu.com/questions/786928/ubuntu-16-04-fstab-fails-with-nobootwait)

---

### Post by steeldriver on 2016-08-23
There used to be a nobootwait option for exactly this situation, but it seems to have been removed - I wonder why?

[http://askubuntu.com/questions/786928/ubuntu-16-04-fstab-fails-with-nobootwait](http://askubuntu.com/questions/786928/ubuntu-16-04-fstab-fails-with-nobootwait)

---

