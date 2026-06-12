---
title: "Repartition Woes"
date: 2007-09-28
forum: General Help
---

### Post by NautArch on 2007-09-28
It turns out I didn't make my linux partition large enough (enjoying the fruits of the Wine).  

I currently have my reiserFS partition, and a couple of NTFS partitions (one for windows system, one for shared files).  

I've tried gparted through ubuntuLiveCD, the gparted LiveCD, and Knoppix.

When going in through UbuntuLive, and i run gparted, my /dev/sda shows up all as one unallocated drive, which ain't true.  WHen i run fdisk -l i get my full list:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3825    30723288+   7  HPFS/NTFS
/dev/sda2            3826        4080     2048287+   5  Extended
/dev/sda3            4081        5736    13301820   83  Linux
/dev/sda4   *        5737       19458   110215361    7  HPFS/NTFS
/dev/sda5            3826        4080     2048256   82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2        9732    78164257+   f  W95 Ext'd (LBA)
/dev/hdc5               2        9732    78164226    7  HPFS/NTFS

GpartedLiveCD doesn't open into the gui and says i have limited console.  Knoppix erros with loop definition.

I want to reduce the size of /dev/sda1 and /dev/sda5 and add the new space to /dev/sda3.

Help! :)

---

### Post by kwilliam on 2007-09-28
On the Ubuntu Live CD, make sure you run gparted using "sudo gparted".

If that is not the problem, I suggest running "fsck" on your filesystem. (From a Live CD.) I was doing some repartitioning today in order to install XP, and had gparted get stuck on the initial "scanning..." step because of a filesystem with errors.  Run "fsck -r /dev/hdX" to check a filesystem for errors and repair it.  (where hdX is hda or hdb or sda or whatever)  If there are a lot of errors, you might want to run "fsck -a /dev/hdX" to repair filesystems without any interactive confirmation.

That may or may not be it - I'm not an expert.  Alternatively, you could try using "parted", which is a non-GUI utility.  I had success with "parted" even when "gparted" was stuck.

---

### Post by Shazaam on 2007-09-28
For some reason the gpartedLiveCd does that to me once in a while. If it happens completely shut down the pc, then boot with the GpartedLiveCd in the drive and chose "Force Vesa" at the splash screen. It should work again.
I had that happen with the Ubuntu LiveCd (unallocated disk) and I panicked and tried using testdisk to recover the partitions and completely trashed the drive. Long story short if fdisk shows the correct geometry try cold booting the livecd again.

---

### Post by bodhi.zazen on 2007-09-28
> **NautArch said:**
> It turns out I didn't make my linux partition large enough (enjoying the fruits of the Wine).  

I currently have my reiserFS partition, and a couple of NTFS partitions (one for windows system, one for shared files).  

I've tried gparted through ubuntuLiveCD, the gparted LiveCD, and Knoppix.

When going in through UbuntuLive, and i run gparted, my /dev/sda shows up all as one unallocated drive, which ain't true.  WHen i run fdisk -l i get my full list:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3825    30723288+   7  HPFS/NTFS
/dev/sda2            3826        4080     2048287+   5  Extended
/dev/sda3            4081        5736    13301820   83  Linux
/dev/sda4   *        5737       19458   110215361    7  HPFS/NTFS
/dev/sda5            3826        4080     2048256   82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2        9732    78164257+   f  W95 Ext'd (LBA)
/dev/hdc5               2        9732    78164226    7  HPFS/NTFS

GpartedLiveCD doesn't open into the gui and says i have limited console.  Knoppix erros with loop definition.

I want to reduce the size of /dev/sda1 and /dev/sda5 and add the new space to /dev/sda3.

Help! :)

use gparted from the gparted Live CD (the version with Ubuntu will not allow you to do what you want and the live gparted CD has a more up-to-date version).

Start gparted with the vesa driver ... +1 Shazaam

If you have the same problem with gparted from the live CD, you will need to re-build your partition table with fdisk. This is a snap as you have the old partition table (you posted it ...)

[How to fdisk](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

You should make the partition table look as it does in your OP when you use "p" with fdisk, then write to disk and exit, reboot, and now re-partition ...

If you make a mistake, either undo or exit without writing.

---

### Post by NautArch on 2007-10-06
Okay, so I tried this and made things worse.  My partition table appears to be Fubar, and fdisk instructions page doesn't seem to help.  My head and cylinder numbers no longer match my previous post.  Can someone point me to some isntructions on how to rebuild my partition table to match what it should be?

---

### Post by bodhi.zazen on 2007-10-06
If you know the old numbers, use fdisk.

fire up fdisk from a live CD, delete all your partitions, and re-build them with the exact same geometry your know to be good.

---

### Post by NautArch on 2007-10-06
that's exactly what i tried, but the cylinder numbers run out at 3880, and i can't match it.  What am i doing wrong?  Is there any other info i can post?

---

### Post by bodhi.zazen on 2007-10-06
Post your original configuration (just to be sure we are on the same page) and the current output of "sudo fdisk -l"

---

### Post by NautArch on 2007-10-06
Sure thing...

CURRENT:

Disk /dev/sda (Sun disk label): 16 heads, 135 sectors, 3880 cylinders
Units = cylinders of 2160 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System

Disk /dev/hdc: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2        9732    78164257+   f  W95 Ext'd (LBA)
/dev/hdc5               2        9732    78164226    7  HPFS/NTFS


ORIGINAL:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 3825 30723288+ 7 HPFS/NTFS
/dev/sda2 3826 4080 2048287+ 5 Extended
/dev/sda3 4081 5736 13301820 83 Linux
/dev/sda4 * 5737 19458 110215361 7 HPFS/NTFS
/dev/sda5 3826 4080 2048256 82 Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 2 9732 78164257+ f W95 Ext'd (LBA)
/dev/hdc5 2 9732 78164226 7 HPFS/NTFS

---

### Post by bodhi.zazen on 2007-10-07
I hope someone with more experience can help , I have not seen a disk change like that.

---

### Post by meierfra on 2007-10-07
You might try[ "testdisk"]("http://www.users.bigpond.net.au/hermanzone/p21.html")  and see whether it can repair your partition table. (Testdisk is  for example on the gparted live cd)

---

### Post by NautArch on 2007-10-07
I'll try testdisk out...is there anything special if i've got sun and intel partitions (reiserfS and NTFS)?

---

