---
title: "Help LVM Volum group can't be found"
date: 2006-09-12
forum: General Help
---

### Post by cemptor on 2006-09-12
I messed up big time, and trying to fiox it before my wife wakes up :(

I have a ubuntu 6.06 32 bit install with LVM. Have (i hope) the following partitions on my first hard disk:

/boot
LVM00/root /
LVM00/home /home
LVM00/music /music
LVM00/pictures /pictures

Also added a new SATA HDD recently, with nothing on it. Added it to my LVM00 Volume Group.

I was happy until I tried to install Windows XP today for my wife (after 6 months of resistance). Came to a partition screen in the XP install, and chose to install Windows on the second HDD. It told me it needed a partition on my primary disk. Wasn't sure what it would do to my GRUB, so I quit using F3 legitimately before installing or partitioning thinking I'd do it later.

Now my Ubuntu does not boot.

I think GRUB is still intact, as the boot process starts. However, it stalls trying to mount the root file system. 

Then I get errors saying "Couldn't find ..." 

One possibility is by choosing to create a partition on my second HDD, which was part of my LVM volume group, I messed up the LVM.

When I boot up using an install CD, and come to manually partition, I can see all the partitions. However, It does not recognize any volume groups.

How do I get out of this hole. Can't afford to lose all that data.

---

