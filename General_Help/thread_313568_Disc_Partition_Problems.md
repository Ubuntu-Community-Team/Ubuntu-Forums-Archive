---
title: "Disc Partition Problems"
date: 2006-12-06
forum: General Help
---

### Post by scottym on 2006-12-06
I have uninstalled Win XP from my dual boot system in order to have a Ubuntu OS exclusively. The problem now is getting The partition that windows was in to be used by Ubuntu. My drive looks like this:

/dev/hda1    ext3    8.59 gigs    (old windows)
/dev/hda3    ext3    6.91 gigs     (Ubuntu)
/dev/hda4    extended  3.13 gigs
  /dev/hda5   ext3                   /home
  /dev/hda6   linus swap

I am trying to avoid a complete reinstall of Ubuntu if possible. Question is can I combine hda1 and hda3 and change the size of hda5 without reinstalling ubuntu? Otherwise how do I use the hda1 now, It is unrecognized by Ubuntu. Do I designate a mount point like in mounting windows? If so how is this done?

Thanks everyone for any help.

---

### Post by scottym on 2006-12-07
Well, apparently no one uninstalls windows on a dual boot setup because there are no answers to my dilemna. ](*,)

---

### Post by rpkehoe on 2006-12-07
sure, you need to get a gparted live cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) reboot into it, and delete the old windows partition, and grow your ext3 partition to take up the space.

---

### Post by scottym on 2006-12-07
Well, that is what I have been trying to do with GParted but it will not delete the partition I had for windows. What I have finally ended up doing is transferring my /home folder to hda1 where windows once resided, hoping then to delete the ext5 i had previously created for /home and the ubuntu swap file. Gparted will not do this claiming I need to unmount the partitions but when I try to unmount partitions it says they are in use and it can't be done. I have played with the /etc/fstab settings and ended up locking myself out of ubuntu completely. I now have ubuntu running again but would like to repartition the drive to more effectively use all of the space in three partitions but Gparted is not cooperating. At some point when I upgrade to the next Ubuntu distro I will repartition everything the way I want it so for the time being I seem to be stuck. It still beats using windows which is on our desktop as a reminder of my hatred for MS and windows.

---

### Post by strabes on 2006-12-07
you can't modify partitions while they're in use. That's why you have to boot into the live CD - so gparted can change them while they're not in use.

---

### Post by scottym on 2006-12-08
Yes, I realize that and was booted in live cd. Sorry to not be clear before but that is where the messages are coming up. In live cd my gparted from the ubuntu install disc will not delete an extended partition that i created because it states that it is in use. Their is a locked symbol next to the dev/hda5 as well. BTW I cannot open gparted unless I am in live cd using sudo. Perhaps in root but I have not tried that in a while.

---

