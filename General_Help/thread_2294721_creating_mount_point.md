---
title: "creating mount point"
date: 2015-09-12
forum: General Help
---

### Post by jason.nickols on 2015-09-12
Having a difficult time trying to get a mount point created for use with clonezilla.  I have my OS drive which is an ssd (ext2), and a 4tb data drive setup with btrfs; the data drive is mounted at /mnt.  I want to create a mount point that can be accessed for clonezilla (pxe boot).  All goes well I start booting into clonezilla when "mount.nfs mount point does not exist /mnt/clonezilla" pops up it goes on a little further and then fails after it again cannot find the mount point.  

So...what i wish to do is create a mount point that can be accessed through pxe that resides on my 4tb data drive (/dev/sdb).  In my fstab right now /dev/sdb is mounted at /mnt to run at boot.  I have a directory named clonezilla within /mnt and need it to be recognized.  Currently, in clonezilla configuration files i am pointing to /mnt/clonezilla but it does not see it.

Fairly new to Linux world and this has been driving me crazy...any suggestions would greatly be appreciated.


Thanks

---

### Post by jason.nickols on 2015-09-12
I think i got it fixed...  here is what i did -- 1. "umount /dev/sdb"  2.  "mount -o subvol=/mnt/clonezilla /dev/sdb"  it seems to see my mount point now.  #2 is a command used for btrfs subvolumes not sure if it is btrfs specific or not for anyone interested obtained my info on how to mount a subvolume from here:  [https://www.howtoforge.com/a-beginners-guide-to-btrfs-p2#-mounting-subvolumes](https://www.howtoforge.com/a-beginners-guide-to-btrfs-p2#-mounting-subvolumes)

now that this is done i have a new issue  ARRRGH!!!  anyway calling this solved.

---

