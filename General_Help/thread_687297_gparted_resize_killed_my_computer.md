---
title: "gparted resize killed my computer"
date: 2008-02-04
forum: General Help
---

### Post by vik.vaughn on 2008-02-04
I did a gparted resize on one of my storage hard drives (no root or home folders on the drive) and the system locked up once the operation completed some five hours later. When I reboot the computer, the progress bar won't even get past the first tick mark. Booting into recovery mode is no good, as soon as I log in, it logs right back out.

I guess I just need a plan of attack here to find out what's wrong and what I need o do to fix it. It seems really weird to me that resizing a drive that is essentially a single media folder could make my machine un-bootable.

---

### Post by kesman on 2008-02-04
Try removing "splash" and "quiet" from the boot options in grub menu. Then you'll at least see what's wrong.

---

### Post by danwood76 on 2008-02-04
Gparted in my experiance isnt very good if you've used other partitioning software on that drive (I think this goes for most partitioning software).

Can you boot with the live CD and try to see whats happened using Gparted from there?

regards,
Danny

---

### Post by vik.vaughn on 2008-02-05
booted into my old feisty cd. gparted can't recognize the partition, and fsck says "bad magic number while trying to open /dev/sdc"

---

### Post by danwood76 on 2008-02-05
whats the output of sudo fidsk -l?

---

### Post by niethslim on 2008-02-05
> **danwood76 said:**
> whats the output of sudo f[COLOR=red]di[/COLOR]sk -l? 

^

---

### Post by vik.vaughn on 2008-02-06
Device: /dev/sdc2
Start: 1
End: 29246
Blocks: 234918463+
Id: 83
System: Linux

Also while trying to fsck /dev/sdc2 instead of just /dev/sdc, I get "fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc2 Could this be a zero length partition?"

---

### Post by kpkeerthi on 2008-02-06
> **vik.vaughn said:**
> booted into my old feisty cd. gparted can't recognize the partition, and fsck says "bad magic number while trying to open /dev/sdc"

Is this the drive you attempted to resize? Did you make sure it was NOT MOUNTED before you resized it?

---

### Post by danwood76 on 2008-02-06
> **vik.vaughn said:**
> 
Also while trying to fsck /dev/sdc2 instead of just /dev/sdc

You wont be able to fsck /dev/sdc as it is not a partition, you can only disk check partitions.

What is the full output of sudo fdisk -l ?
you may have a messed up partition table and it would be nice if we could see the details to help correct the situation.
It is possible to rebuild the partition table with fdisk if its damaged (which is most probably the case)

regards,
Danny

---

### Post by vik.vaughn on 2008-02-06
> Is this the drive you attempted to resize? Did you make sure it was NOT MOUNTED before you resized it?

It's not possible to make changes with gparted on a mounted drive.

> What is the full output of sudo fdisk -l ?
you may have a messed up partition table and it would be nice if we could see the details to help correct the situation.
It is possible to rebuild the partition table with fdisk if its damaged (which is most probably the case)

Sorry I wasn't able to post the full output, I was posting from my laptop while working off the ubuntu live cd on my desktop so I couldn't cut and paste. I will get the ubuntu box online tonight and post the full outbput.

---

### Post by vik.vaughn on 2008-02-18
ok, so now it's taking a REALLY long time to boot into the live cd. I keep getting buffer i/o errors on the sata drive I'm having a problem with (sdc2.)

So here is the output from sudo fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8414    67585423+   7  HPFS/NTFS
/dev/sda2            8415        9729    10562737+   7  HPFS/NTFS

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2808    22555228+   f  W95 Ext'd (LBA)
/dev/sdb4            2809       12187    75336817+   c  W95 FAT32 (LBA)
/dev/sdb5               1         192     1542177   82  Linux swap / Solaris
/dev/sdb6             193        1272     8675068+  83  Linux
/dev/sdb7            1273        2808    12337888+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2               1       29246   234918463+  83  Linux

```

fsck output:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc2
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc2
Could this be a zero-length partition?
```

---

### Post by danwood76 on 2008-02-19
Do you have a lot of stuff on that HD? Is it old?

I would think that this disk is either:
a. Dying
b. Has bad sectors/partition table/MBR

If you dont have much on there or you can back it up I would erase the hard disk completely with a boot CD and start again.

---

### Post by vik.vaughn on 2008-02-19
That is my media drive. Around 150GB of stuff I love. I've got a lot of weird music on there I'll probably never be able to get again.

How can I repair it? If that doesn't work, how would I be able to mount it to back up the data that is there?

Resizing that partition without backing it up was DUMB. I'll never make that mistake again.

---

### Post by danwood76 on 2008-02-19
You could have a go at rebuilding the partition table.
It wont affect the data on the drive and may possibly lead to you getting data back.

One of the things you will probably need to do is backup the MBR so you can restore it if you completely destroy the partition table (which you will be doing)
this is done with the following command:
```

dd if=/dev/sdc of=MBR-backup bs=512 count=1

```
you will also need to be in a directory you can write to, otherwise the backup is pointless.

you can then think about rebuilding the partition table.
fdisk is the tool I would use for this.

```

sudo fdisk /dev/sdc

```

then you want to create a new partition table with the first primary partition taking up the entire drive, and being linux.

Im not 100% sure on the options at this point but you do it in this order:

create new partition table -> new primary partition -> entire drive (reccomended start and stop locations) -> change partition type to linux (0x83)

you can press m I think it is to get the available options in fdisk.

This will create a single linux partition the size of the disk, you then want to save the changes to the disk and restart.
You should then in theory be able to mount the drive and it might work as it did before.

The above commands assume the disk is /dev/sdc if its different you need to change the commands appropriantly

The buffer i/o errors could be a sign of a dying drive though but its worth a shot.

---

### Post by vik.vaughn on 2008-02-19
Dan, first of all I want to thank you for your help.

I created a new partition, rebooted to my live cd, and it appears in "sudo fdisk -l" but I still cannot mount it. Gparted also doesn't recognize the partition. Any ideas before I blow the drive away? (actually I may be throwing the drive away.)

I don't know if this matters or not, but I had toyed with the idea of using LVM a while back for this very purpose, dynamic partition resizing. I don't know if I ever ended up formatting this drive with LVM, but if I did, would that have caused any of these problems? Would gparted have recognized it as an LVM partition and left it alone?

By the way, I have to boot to a live cd because my regular gutsy install hasn't booted since I resized the partition and it locked up (immediately after resizing) a few weeks ago. That may be a separate issue entirely that I'll tackle later.

---

