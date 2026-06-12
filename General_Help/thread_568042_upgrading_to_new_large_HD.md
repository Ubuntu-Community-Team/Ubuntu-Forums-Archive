---
title: "upgrading to new large HD"
date: 2007-10-05
forum: General Help
---

### Post by bill45 on 2007-10-05
My Ubu system must grow as it gradually supplants my Win boxes.  I'll soon have a spare 80GB drive to replace my current 20GB in the old Dell.  What utils / methods must I use to move my current install image to a larger drive? 

Bill C

---

### Post by vanadium on 2007-10-05
Just providing conceptual ideas. Depends on your experience and the risk you want to take. In principle it should be possible to mirror your partition to the new drive using the dd command. After that, you would need to install grub and tell it to boot from the partition on your new drive. /etc/fstab should be ok if UUIDs are used, even if the partition name is different. The dd command indeed mirrors the partition, including the UUID. In order to prevent problems with swap, you would disable the swap first on your old install, then copy your partition on the new drive. Once the system can boot on the new drive, you can create a swap partition on the new drive and reenable the use of a swap. Alternatively, you would dd the swap as well, but that would require more time to copy essentially meaningless data.

---

### Post by bill45 on 2007-10-06
Thanks Vanadium.  Good reply with several commands and terms for me to look up and study.  You might find amusing; I have recovered Win boxes by installing from sys CD, overwriting new install with old mirror.  Can something like this be done in the following order - do some kind of minimal install so that GRUB and Swap are set up on "new" drive, then overwrite with image from smaller drive?  


Alternative is to keep old drive as is and install 2nd drive as data storage.  Is it acceptable to place the HOME, USERNAME and other users directories on a second drive?  I know it is possible to mount any directory anywhere desired, but is it advisable?

Bill

---

### Post by ramjet_1953 on 2007-10-06
There are a couple of other options.

1. Ghost For Linux (G4L) offers a local clone option.

Here's a link: [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have used this and it produced a perfect 1:1 copy, including GRUB.

There is a downside, however, in that it is slow, as it copies even blank sections of your HDD.

2. CloneZilla also offers a local clone option.

Here's a link: [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

I have not used it, but have been told it is very reliable and is much quicker than G4L, as it only copies sectors with data in them.

Both programs are iso images that you burn slowly to a CD and then boot your system from them.

Regards,
Roger 8)

---

### Post by vanadium on 2007-10-07
The disadvantage of G4L, being slow as it copies also "empty" data, is the same for dd. That also will copy all of the partition, including empty data.

bill45, the swap might again be the problem. The UUID of the swap of your "minimal" install will certainly be different than that stored in your image. Again, it would be preferable to have a mirror where the swap is disabled in order to be able to reenable it once the mirror is in place on the new partition.

Your alternative is perfectly acceptable and advisable: you are doing no more than using the flexibility of linux to configure the system to your needs. Even more: performance wise and safety wise, it is a very good approach for anyone who has two permanent disks in his system.

---

### Post by bill45 on 2007-10-08
Thanks for links and advice Roger and Vanadium.  Plenty of hard tack to chew on here.  Up to now the Ubu is the 2nd son hand-me-down box but change may be in the offing.

---

### Post by Shazaam on 2007-10-08
More food for thought.
With my sometimes ballpeen hammer approach to O/S's I have loaded up the gparted livecd and copied/pasted partitions between drives; even did this going from a PATA to an SATA drive and I haven't had any problems yet. Not reccomended though :)
Upon furthur thought that is probably a gui for the dd command.

---

