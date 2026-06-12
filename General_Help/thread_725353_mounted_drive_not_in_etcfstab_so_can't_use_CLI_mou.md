---
title: "mounted drive not in /etc/fstab so can't use CLI mount"
date: 2008-03-15
forum: General Help
---

### Post by ubuntooey on 2008-03-15
I have installed Ubuntu on an external drive. Mac OS X is on my internal SATA drive, which is  /dev/sda2. The GUI for Places/Computer shows the internal drive, both when mounted and unmounted. However, it mounts it read-only, and I would like to write to it.

I have tried sudo mount -w /dev/sda2, but it complains that /dev/sda2 is not in /etc/fstab or /etc/mtab. What should I do?

---

### Post by mikewhatever on 2008-03-15
/dev/sda2 is probably a partition on the internal HDD. Post some more info:
<sudo fdisk -l>
<cat /etc/fstab>

Check this too [http://www.google.co.il/search?q=ubuntu+mount+external+hard+drive&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a.:](http://www.google.co.il/search?q=ubuntu+mount+external+hard+drive&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a.:))

---

### Post by logos34 on 2008-03-15
what about 
sudo umount /media/sda2 (or whatever the mount point is)

**sudo mount -t hfsplus /dev/sda2 /media/sda2** (if necessary do mkdir /media/sda2 to create mountpoint)
(or use just hfs for fiesystem type)

does that give you you write access?

---

### Post by ubuntooey on 2008-03-15
The output of sudo fdisk -l (the relevant part) is

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007ea5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26        9713    77814832   af  Unknown


/etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=2006953a-8d0a-45e7-8d47-ea8eaf590159 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2860-11F4  /media/EFI      system  partition       vfat    defaults,utf8,umask=007,gid=46 0 1
# /dev/sdb6
UUID=bc32c75e-7f8d-4340-ab0d-c53c2786c6d9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


logos34, I tried your suggestion. I got

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


So I did dmesg | tail and got 

[18445.084000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[18445.084000] hfs: failed to load extents file

But I don't know flag for the force option. I also tried various HFS tools, to no avail. Thanks so much for your help.

---

### Post by robertchahine on 2008-03-15
i had a problem like this, but when i installed the gparted from add/remove, everything woked normal

---

### Post by ubuntooey on 2008-03-18
Turns out I had an HFS+ journaled partition, and the Linux kernel doesn't have support for HFS+ journaled writing. Thanks for all help.

---

