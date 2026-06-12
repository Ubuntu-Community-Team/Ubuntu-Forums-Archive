---
title: "Cannot resize partition"
date: 2015-09-04
forum: General Help
---

### Post by zair2 on 2015-09-04
Hi there,

I have a 165GB Xubuntu installation that I would like to dual boot with another Linux distro or Windows. For that, I need to shrink the Xubuntu partition, however I have been trying for the past few days and I cannot get it to work so I would appreciate any help here. Previously, it showed gparted showed that I was using 165GB out of 165GB disk space (when I wasn't) - I remedied this by following a guide on lvm resizing, but I still can't seem to shrink the partition. I have tried using a LiveCD and deactivating the partition and shrinking it (still doesn't work - I will post the error details on this later, in a rush right now!), I've tried deleting the boot partition (the only other partition that shows up in gparted) and shrinking it; this does not work either.

Here are the error details when I try to shrink using gparted whilst using Xubuntu (not on the LiveCD):

GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize
 Libparted 2.3
 [TABLE]
[TR]
[TD="colspan: 2"] **Shrink /dev/sda5 from 153.15 GiB to 122.00 GiB**  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda5  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda5
start: 501760
end: 321671167
size: 321169408 (153.15 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] shrink file system  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***lvm pvresize -v  --setphysicalvolumesize 127923200K /dev/sda5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]  0 physical volume(s) resized / 1 physical volume(s) not resized
[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]    Using physical volume(s) on command line
    Archiving volume group "xubuntu-vg" metadata (seqno 4).
    /dev/sda5: Pretending size is 255846400 not 321169408 sectors.
    Resizing volume "/dev/sda5" to 321169408 sectors.
    Resizing physical volume /dev/sda5 from 0 to 31231 extents.
  /dev/sda5: cannot resize to 31231 extents as later ones are allocated.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 ========================================

I will appreciate any help, but I am quite a novice at Linux so please be patient with me!


EDIT: When attempting from LiveCD:

Error details when attempting to shrink the deactivated volume via gparted in Xubuntu LiveCD:

GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize
 Libparted 2.3
 [TABLE]
[TR]
[TD="colspan: 2"] **Shrink /dev/sda5 from 153.15 GiB to 124.05 GiB**  00:00:01    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda5  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda5
start: 501760
end: 321671167
size: 321169408 (153.15 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***lvm pvck -v /dev/sda5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]  Found label on /dev/sda5, sector 1, type=LVM2 001
  Found text metadata area: offset=4096, size=1044480
[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]    Scanning /dev/sda5
    Found LVM2 metadata record at offset=7168, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=5632, size=1536, offset2=0 size2=0
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] shrink file system  00:00:01    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***lvm pvresize -v  --setphysicalvolumesize 130073600K /dev/sda5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]  0 physical volume(s) resized / 1 physical volume(s) not resized
[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]    Using physical volume(s) on command line
    Archiving volume group "xubuntu-vg" metadata (seqno 4).
    /dev/sda5: Pretending size is 260147200 not 321169408 sectors.
    Resizing volume "/dev/sda5" to 321169408 sectors.
    Resizing physical volume /dev/sda5 from 0 to 31756 extents.
  /dev/sda5: cannot resize to 31756 extents as later ones are allocated.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 ========================================



FINAL EDIT: SOLVED. SEE LATEST POST FOR INFORMATION.

---

### Post by Bucky Ball on 2015-09-04
*Thread moved to **General Help**.*

Don't know if this helps, but you can't resize a mounted partition and you can't unmount the partition you are running the OS from.

Therefore, boot live media (USB or disk), 'Try Ubuntu', launch Gparted, make sure the Xubuntu disk is unmounted by right clicking it, resize.

It goes without saying that you should have reliable backups of anything you don't want to lose prior to doing this ... just in case. :)

Good luck.

PS: Resizing an LVM partition? The black arts which I have no knowledge of.

---

### Post by patlkli on 2015-09-04
> **Bucky Ball said:**
> 
Don't know if this helps, but you can't resize a mounted partition and you can't unmount the partition you are running the OS from.


Actually you CAN resize a partition online, even while it's mounted and even if it's the root partition, but sadly, you can only enlarge it online, not shrink it. (NB: Not all filesystems support this, but the default ext2/3/4 do).

> **zair2 said:**
> 
I have tried using a LiveCD and deactivating the partition and shrinking it (still doesn't work - I will post the error details on this later, in a rush right now!)


The error is quite expected, since you can't shrink partitions online. You have to do the partitioning from a Live-CD and if that really doesn't work, the error details would be quite helpful in order to give some advice.

---

### Post by zair2 on 2015-09-04
Error details when attempting to shrink the deactivated volume via gparted in Xubuntu LiveCD:

GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize
 Libparted 2.3
 [TABLE]
[TR]
[TD="colspan: 2"] **Shrink /dev/sda5 from 153.15 GiB to 124.05 GiB**  00:00:01    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda5  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda5
start: 501760
end: 321671167
size: 321169408 (153.15 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***lvm pvck -v /dev/sda5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]  Found label on /dev/sda5, sector 1, type=LVM2 001
  Found text metadata area: offset=4096, size=1044480
[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]    Scanning /dev/sda5
    Found LVM2 metadata record at offset=7168, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=5632, size=1536, offset2=0 size2=0
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] shrink file system  00:00:01    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***lvm pvresize -v  --setphysicalvolumesize 130073600K /dev/sda5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]  0 physical volume(s) resized / 1 physical volume(s) not resized
[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]    Using physical volume(s) on command line
    Archiving volume group "xubuntu-vg" metadata (seqno 4).
    /dev/sda5: Pretending size is 260147200 not 321169408 sectors.
    Resizing volume "/dev/sda5" to 321169408 sectors.
    Resizing physical volume /dev/sda5 from 0 to 31756 extents.
  /dev/sda5: cannot resize to 31756 extents as later ones are allocated.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 ========================================


EDIT: I just ran lvscan and notice that there is a swap volume hidden inside the logical volume, I'm going to delete it and try resizing - this SHOULD work!

EDIT2: After some tinkering around, it finally worked, thanks for all the help!

---

### Post by zair2 on 2015-09-04
I'll put my solution in another post for anyone who encounters the same problem:

I could not resize my lvm partition because there was a hidden swap volume hidden inside the logical volume that gparted couldn't see. I therefore ran lvmscan and it showed me TWO lvm partitions - one for my actual file system and a swap lvm partition. I deleted this partition by running:

```
# lvm lvremove /dev/VolGroup00/swap_1
```

 and removed the corresponding entry in the fstab file. This then allowed me to shrink the partition and I haven't yet decided if I am going to recreate a swap partition or not.

---

### Post by Bucky Ball on 2015-09-04
@zair2: Please use default font, point size and colour and use code tags for terminal output. See last link in my signature.

If your issue is solved, please see the first link in my signature.

Don't post another post with the solution. Makes no sense. Put it here where it is related to the original problem and mark the thread as solved. Thanks. Good luck.

---

