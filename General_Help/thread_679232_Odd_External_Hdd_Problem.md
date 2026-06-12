---
title: "Odd External Hdd Problem"
date: 2008-01-26
forum: General Help
---

### Post by nazeemlinux on 2008-01-26
Hello guys, i had a very weird problem with my External Hdd while installing Ubuntu 7.0 using the Live CD. I have a 160GB HD and a Freecom 400GB Ext Hdd. I installed Ubuntu on a partition on the int Hdd(the 160Gb one), it installed successfully and i was able to launch it. But my Ext Hdd was found unmounted, it was empty and all the space was free. What dp i have to do to get ALL my files back?Plz help me, am a total n00b in Ubuntu!Thx

---

### Post by taurus on 2008-01-26
You have files on the external harddrive and you want to access them?  Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by nazeemlinux on 2008-01-26
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98049804

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2254    18100568+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2255        9548    58589055   83  Linux
/dev/sda3            9549        9733     1486012+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a13af

   Device Boot      Start         End      Blocks   Id  System

Its the 400Gb one thats not working, i have very important files on it!!!!Plz help

---

### Post by taurus on 2008-01-26
Doesn't look like there is any filesystem on that drive, /dev/sdb?  Since you still have windows on that machine, why don't you boot into windows and see if windows can read your external drive?

---

### Post by nazeemlinux on 2008-01-26
Yeah i tried to, but its still the same!I guess i have to format it but in that case i will lose all my important data, which i dont want to. What do u think might have caused the problem?

---

### Post by mc4man on 2008-01-26
You probably deleted the partition table on the external hdd, if so, all your data is still there. While any professional service could fix this the cost might be much more than it's worth. You could ck. out this program - the demo won't restore anything but could show you what's there. The paid version, well you'd have to decide.
[http://www.partition-recovery.com/](http://www.partition-recovery.com/)

---

### Post by nazeemlinux on 2008-01-27
I reformatted the disk in Windows and running a recovery on it. Am using Runtime Software GetDataBack for NTFS. I haven't been able to restore the data yet, I will post the feedback when am done with it.Thx 4 ur help guys, really appreciated it :)

---

