---
title: "Unable to mount"
date: 2013-06-13
forum: General Help
---

### Post by BuddyThirteen on 2013-06-13
When inserting a USB flash drive (named "Sexy"), I'm getting an error message that indicates the drive can't be mounted.> Error mounting /dev/sdb1 at /media/johnny/Sexy: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/johnny/Sexy"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or sorunning dmesg|tail results in:> [ 1108.935236] scsi 8:0:0:0: Direct-Access     pny      USB 2.0 FD       1.00 PQ: 0 ANSI: 4
[ 1108.936508] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 1108.938594] sd 8:0:0:0: [sdb] 62816256 512-byte logical blocks: (32.1 GB/29.9 GiB)
[ 1108.940569] sd 8:0:0:0: [sdb] Write Protect is off
[ 1108.940583] sd 8:0:0:0: [sdb] Mode Sense: 2f 00 00 00
[ 1108.942566] sd 8:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1108.950402]  sdb: sdb1
[ 1108.957015] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 1109.869095] EXT4-fs error (device sdb1): ext4_iget:3743: inode #8: comm mount: bad extra_isize (44587 != 256)
[ 1109.869107] EXT4-fs (sdb1): no journal foundAnd of course it was right when I'd copied a bunch of important stuff to this drive, and I haven't yet gotten to back it up. So yeah.

Is it recoverable, or am I just completely out of luck?

---

### Post by BuddyThirteen on 2013-06-14
So...?

---

### Post by 3rdalbum on 2013-06-14
You could try running fsck on the device? Is it formatted Ext4, by the way? That is what it is being detected as, but usually flash drives are preformatted as Fat32 (vfat).

---

### Post by BuddyThirteen on 2013-06-14
Yes, I reformatted it as ext4 because I needed to create a truecrypt container that was about 6GB.

Running fsck, it says:
> fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
Superblock has an invalid journal (inode 8).
Clear<y>? 
So, do I want it to clear?

---

