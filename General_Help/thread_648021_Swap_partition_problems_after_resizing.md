---
title: "Swap partition problems after resizing"
date: 2007-12-23
forum: General Help
---

### Post by karusho on 2007-12-23
Backstory:

After making sure that everything was running smoothly on Ubuntu and an XP VM on virtualBox, I decided to completely wipe Vista off of my laptop (Sony VAIO VGN-NR160E/S).  After this, I moved and resized the Ubuntu partition to 80GB to fill the void from the Vista partition.  I also moved and resized an NTFS partition I had been using as a neutral ground between my Vista, XP on virtualBox, and Ubuntu to just under 60GB, and I ended up with 1.5GB extra space, so I expanded my 512MB swap partition up to 2GB.  After that, I started experiencing the problems.

When I first closed the lid to hibernate it, I noticed that it didn't turn off for a while.  I opened the lid and found that it had not shut off at all, and that it displayed the locked screen window.  I logged back in, and a pop up said that hibernation had failed.  I went into GParted and noticed that I had forgotten to swapon the swap partition.  I did so, and tested the hibernation.

Didn't work.  This time, I'm guessing it properly saved to the swap partition, but when it booted up again, it had started Ubuntu afresh.  I opened up GParted, and saw that the swap partition was no longer on.

I opened the terminal, and typed sudo swapon /dev/sda2.  Hibernate, shut off, turn on, nothing.  I open terminal, type free, and:
```
patrick@patrick-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1026300     648472     377828          0      17132     348508
-/+ buffers/cache:     282832     743468
Swap:            0          0          0

```

  I fiddled around in /etc/fstab (something I probably should not have done, but I made a backup) and this is the current state its in:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=afc87147-55e6-4233-aab4-9ce6929201fc none            swap    sw              0       0
# /dev/sda3
UUID=8b609dbb-aff1-4c71-8129-4e10251b0fd7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1517742D4BE06428 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Now, I need to be able to hibernate, as I often have limited time to finish doing as much as I can on something.  Unfortunately, every time the machine turns off, the swap partition goes kersploot.

Would someone please kindly help me with permanently turning on the swap partition?

---

### Post by bingoUV on 2007-12-23
Are you sure the UUID of the swap is correct in the fstab file. Verify by 
```

blkid /dev/sda2

```

Then change the mount options sw to defaults. i.e.
```

UUID=afc87147-55e6-4233-aab4-9ce6929201fc none            swap defaults 0       0

```

---

### Post by karusho on 2007-12-23
I did that, and I fixed the UUID.  I restarted, and it mounted the swap partition fine.  I closed the lid to hibernate, when I turn it back on, it starts ubuntu afresh.  The swap partition is no longer recognized (in GParted it says filesystem is 'Unknown', I can't do swapon).

EDIT:
Do you think the problem could be caused by partition table entries not being in order?
```
patrick@patrick-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9b14617

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         963     7727104   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2           19196       19457     2104515   82  Linux swap / Solaris
/dev/sda3   *         964       11406    83883397+  83  Linux
/dev/sda4           11407       19195    62565142+   5  Extended
/dev/sda5           11407       19195    62565111    7  HPFS/NTFS

Partition table entries are not in disk order

```

---

### Post by karusho on 2007-12-24
*BUMP* and update:

I decided to shove my swap back into the extended partition, because that's what worked before.  Still same problem.

---

### Post by logos34 on 2007-12-24
I was having the same problem recently until I switched to x64 ubuntu studio 7.10.  Seems to have gone away.

But on 32-bit gutsy hibernate was constantly failing and/or the swap failing to mount at boot...because of the black triangle in gparted I had to reformat it each time.  I was not using the UUID format either in fstab.  Since it was on a logical I tried it on a primary, but no difference.  I still wonder what the issue was.

---

### Post by karusho on 2007-12-24
*sigh*

I guess I'll just reinstall and hope for the best, and hope 8.04 has this problem fixed.

---

