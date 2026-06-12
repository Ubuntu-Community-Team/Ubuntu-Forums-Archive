---
title: "Partitioning Mess...Please Help!"
date: 2007-06-17
forum: General Help
---

### Post by bpont on 2007-06-17
I used gparted to destroy a primary, logical and swap partition.  I then created a new swap partition (doubling its previous size), applied changes and swapon.  It worked.

I then created two ext3 partitions from the unallocated space freed from the deleted primary/logical partitions and when I applied changes, only one of those partitions was being read and the other was listed as 'unknown'.  I repeated the process several times, even with different file systems and deleting / recreating, etc. to no avail.

I deleted the two newly created partitions (ext3 and 'unknown') and then closed out of gparted and ran cfdisk instead.  I created one new primary partition from the unallocated space and gave it an 8E (LVM) filesystem and wrote the partition table.  I got a message that the table was written but could not be reread and to reboot system to apply changes.

I rebooted and fsck borked on me (from I'm assuming the /etc/fstab being unedited from all the changes) and brought me to some 'file repair shell' that I had no idea what to do with.  I opened nano at the cmd line and stripped out the old unneeded lines from fstab, I wasn't sure what the hell to do about the swap line because in the good old days, I could have just changed the /dev/hda-whatever, but now everything is UUID-etc. etc., so I didn't know what to do and so left it alone.  Then I rebooted.  The system booted up with no fsck errors this time and i got to the login screen and then ran 'top' to see if my swap was on...it wasn't.  Now with only 512mb ram I have no swap available.  

But it gets worse.

I opened up gparted to check the table and it now lists the entire disk as unallocated!  If i check the partition table in cfdisk, everything looks as it should.  WTF??

I should mention that I didn't touch the / partition, so everything related to the Ubuntu install should be fine (I'm assuming).

So now I'm left wondering / confused:

Why is my partition table correct in cfdisk and unrecognized in gparted?  How do I correct it?

How can I edit my /etc/fstab to recognize my new swap partition (/dev/sdb6)...I have no clue about the UUID format's usage. Even if I run swapon, I get this:
```

$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/c807b423-3da6-4efd-911f-61e6d8b78d3d: No such file or directory
```

The whole upshot of this is that I was trying to created a volume group to mount /home on and now I'm in a terrible mess.  Any help would be appreciated.  :(

---

### Post by jfrorie on 2007-06-21
I can confirm that gparted is having some problem with swap.  I expanded my swap by 1GB and gparted worked fine, until reboot. Now, neither my system or gparted recognize my swap and I have to manually reformat it every time and swapon on every load.

I read another post from someone that had a similar problem.  He formatted the swap as ext2, rebooted and then formatted as swap.  This solved his problem, but I have had no success.  Does this work for you?

Jim

---

