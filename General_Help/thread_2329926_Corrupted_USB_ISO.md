---
title: "Corrupted USB ISO"
date: 2016-07-06
forum: General Help
---

### Post by hornetster on 2016-07-06
Trying to write a Ubuntu ISO (have tried both 16.04 Desktop i386 + Server i386) to a USB drive, and whatever/however I do it, I end up with a corrupted USB drive - in GParted, shows as "File System": unknown, with flags boot and hidden, and anything else seems to want me to format the drive.
Have tried writing using dd and StartUP Disk creator, with the same outcome. Thought it may have been because the drive was mounted (as Ubuntu automatically mounts the USBs), so have ensured it is not, by manually umounting at the command line - no change.
BUT, if I reboot my computer into Opensuse, can dd fine to a usable (same hardware) USB boot drive.
Anyone have any ideas?
Thanks.

---

### Post by sudodus on 2016-07-06
Gparted cannot read a USB boot drive correctly (when created by the cloning method). That does not prevent it from working.

Please try to boot the computer from it, and tell us the result :-)

You can also try mkusb according to this link: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Read more about creating USB boot drives and booting from USB at this link: [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by hornetster on 2016-07-06
Hmmm... Ok that DOES seem to work, but tried before without umounting, and I'm sure it didn't work, so the umounting must be the difference...??
Might have a bit more of a play.
Thanks!

---

### Post by sudodus on 2016-07-06
Yes, the partitions on the target drive should be unmounted when you clone the iso file to it.

This (and a 'safety belt around dd' to help avoid writing to the wrong drive) is catered for in mkusb.

---

