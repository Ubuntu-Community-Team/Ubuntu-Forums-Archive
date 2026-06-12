---
title: "Windows wiped the MBR, and installer doesn't see LVM groups??"
date: 2006-07-13
forum: General Help
---

### Post by illynova on 2006-07-13
Hey all,

I recently had the joy of windows overwriting my grub bootloader, so I started googling all around to figure out how to reinstall grub. Not too hard, I figured.... nothing could be further from the truth!


Okay, first off I've tried every variation of loading a live cd, mounting my root partition (hda5), chrooting into it and then running grub-install /dev/hda

The problem is once I enter into a chroot, all of my partitions inside of /dev/ dissapear! I don't know how to fix this.

After some more googling, I came across this thread: [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

It seemed like a good idea, but once I got to the disk manual partition, none of my partions show up! All it says is "IDE1 master (hda) - 30.0 GB TOSHIBA MK3021GAS"

??? I jumped into another console, and looked in /dev. It found all of my partitions (hda1 - ntfs, hda2 - extended , hda3 - swap , hda5 - linux [its reiserfs])


I think it might be because I installed LVM (though I'm not sure, its been awhile and I haven't paid attention since)... does anybody have ANY clue? I can back everything up and reinstall.... but I spent almost a year now configuring and tweaking everything. I *really* don't want to lose all my work.


PLEASE HELP! :)

---

### Post by illynova on 2006-07-13
Not sure if this helps, but when I run a fdisk -l from the install cd, here's what I get


/dev/hda1   ... hpfs/ntfs
/dev/hda2   ... extended
/dev/hda3   ... swap
/dev/hda5   ... linux



If I do a chroot into hda5, and run grub install I get this:
sh03.1# grub-install /dev/hda
/dev/hda: Not found or not a block device

If I try to run grub (inside of chroot) by itself, and do this...
grub> root(hd0,5)
Error 21: Selected disk does not exist

---

