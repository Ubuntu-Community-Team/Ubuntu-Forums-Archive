---
title: "Converting ntfs to ext3"
date: 2008-03-16
forum: General Help
---

### Post by 321.george on 2008-03-16
I have two hard drives in my machine one runs ubuntu and the other is my old windows hard drive. I am trying to convert the windows drive from ntfs to ext3 using

mkfs.ext3 /media.disk

But I get the following message

mkfs.ext3: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.

I'm a bit of a noob and any help would be greatly appreciated.

---

### Post by jocko on 2008-03-16
> **321.george said:**
> I have two hard drives in my machine one runs ubuntu and the other is my old windows hard drive. I am trying to convert the windows drive from ntfs to ext3 using

mkfs.ext3 /media.disk

But I get the following message

mkfs.ext3: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.

I'm a bit of a noob and any help would be greatly appreciated.

You need to specify an actual partition (something like /dev/sdb1 or similar), not the folder it is mounted to.
To figure out which partition, use this command:
```
sudo fdisk -l
```This will list all your hard drives and partitions.
Look for which partition contains your ntfs file system. If it looks like this:
```
    Enhet Start     Början        Slut     Block    Id  System
/**dev/sdb1**               1       14946   120053713+  83  **HPFS/NTFS**

``` Then /dev/sdb1 is the one you want to change.
If that partition is mounted, you need to unmount it:
```
sudo umount /dev/sdb1
```
Then:
```
sudo mkfs.ext3 /dev/sdb1
```

[SIZE=4][COLOR=Blue]Note: Make sure you are certain you run this on the correct partition, and that you have backed up all data you may have on that partition.[/COLOR][/SIZE]

---

### Post by durand on 2008-03-16
you could always use gparted...
```
sudo aptitude install gparted
```

---

