---
title: "installing and mounting a floppy drive!"
date: 2007-12-28
forum: General Help
---

### Post by AvengingAngel718 on 2007-12-28
I ripped a floppy drive out of an old computer that i was salvaging for parts (turned it and another one into a frankenputer running Xubuntu for my girlfriend) and since my computer didnt come with a floppy drive, i decided to install it in mine. I know it's a totally useless and dated format, but i just thought it would be fun and i wanted to. I hooked it all up and booted my computer, then went through the whole new hardware detected thing in my system setup thingy (not in ubuntu) and then logged in to ubuntu. I figured this had made it functional, but i guess not :( anyways, the floppy drive will show up in my file system ONLY when a disk is in it, but if i try to open it it takes a long time then tells me it cant be mounted.

any advice?

---

### Post by ajmorris on 2007-12-28
Hi,
once the disk is inserted into the floppy drive, could you please post the output of ```
sudo fdisk -l
```

---

### Post by AvengingAngel718 on 2007-12-28
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe08d558

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19293   154970991   83  Linux
/dev/sda2           19294       19457     1317330    5  Extended
/dev/sda5           19294       19457     1317298+  82  Linux swap / Solaris


i think it might actually be working, but it wont let me write to the disk. no matter how tiny a file is, when i try to write it to the disk it says it wont fit :/

---

