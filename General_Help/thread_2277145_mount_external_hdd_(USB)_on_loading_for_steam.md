---
title: "mount external hdd (USB) on loading for steam"
date: 2015-05-07
forum: General Help
---

### Post by reader-of-dream on 2015-05-07
I used example with /etc/fstab in Ubuntu 14.10:

UUID=XXXXXXXXXXXXXXX                    /mnt/MyPass     ntfs-3g           default         0   0

It worked nice, I had a choice to skip mount if drive was not present.
In 15.04 I don't have this choice, I wait for 90 seconds while system trying to find hdd (it actually plugged).
Sometimes it works, sometimes doesn't, sometimes I changed usb port and hdd started to mount on loading.

I need it for steam.

---

### Post by ajgreeny on 2015-05-07
I am not certain, but I think you may be able to use the **noauto** option to overcome that delay, which should mean that partition is ignored without any error if it is not attached.

---

### Post by reader-of-dream on 2015-05-07
Yes, I tried it, but the problem is not about a waiting time. I didn't do anything, several days it worked good, but now it doesn't plug my external HDD on loading.

---

### Post by reader-of-dream on 2015-05-09
I've found the way. 
I used program disks:
1. found my external HDD.
2. made some edit in mount options:
a) nofail,auto,rw,user - parameters
b ) I selected a field /dev/disk/by-uuid/********* in Identify As

So, this program added new line to my /etc/fstab:
/dev/disk/by-uuid/4E1AEA7B1AEA6007 /mnt/MyPass ntfs-3g nofail,auto,rw,user 0 0

and not it works each time.

---

