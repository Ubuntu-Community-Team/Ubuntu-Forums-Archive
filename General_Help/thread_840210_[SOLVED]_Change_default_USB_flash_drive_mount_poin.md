---
title: "[SOLVED] Change default USB flash drive mount point?"
date: 2008-06-25
forum: General Help
---

### Post by neur0 on 2008-06-25
Hi,
When I plug in an USB flash drive, Ubuntu auto-mounts it in /media/<volume name>, or in my case /media/KINGSTON, the other thumb drive is mounted in /media/disk. 
Is there any way to change this so it gets mounted to something more predictable/uniform like sdb1, sdc1... or usb1, usb2 ... ?

---

### Post by erginemr on 2008-06-25
None that I know...

I guess you are looking for a way to stabilize the location of your media files for the media viewers/players. But the removable drivers are handled by udev daemon, which are automatically named according a set of rules, which are kept in a series of config files under "/etc". So, it would be a difficult achievement to say the least.

---

### Post by timcredible on 2008-06-25
it'll mount to /media/<name of the partition> or, if it's not named, /media/disk then the next one is /media/disk-1, etc. etc.  so, if you want flash drives mounted to a certain place, just name the partition on the flashdrive via the partition editor, gparted, which is in synaptic.

---

### Post by neur0 on 2008-06-25
Thanks,
Ok, that did solve the problem with my thumb drives, however I can't predict the partition names of other peoples thumb drives.
I'll keep this unsolved for a day in case there are other suggestions. 
Other then other people's USB drives, its solved/worked around.

---

### Post by dalesd on 2008-07-10
I used the instructions here to change the name of my SD card so it will mount to the same point every time.
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

