---
title: "GRUB issues when connecting two HDDs"
date: 2007-12-06
forum: General Help
---

### Post by MyDearWatson on 2007-12-06
Well I guess I should start with the backstory...

A while ago I had an XP machine with some irreplaceable files, and I partitioned it to install Ubuntu 6.  I had to reinstall Ubuntu a few weeks later and I accidentally made the XP partition a Linux swap.  It didn't format the partition, just made it impossible to get to through Windows.  I put away the hard drive for a while and forgot about it for a while.

Now I dual-boot XP and Gutsy and I realized that I could now connect that old IDE HD and retrieve my files thanks to Ubuntu.  Here comes the problem.

I have two SATA HDs in my case now, one of them has a partition with Ubuntu and the other is just an XP partition.  When I connect the old IDE HD, it gives me a GRUB error at startup and I can't boot into either OS.  I tried making it a slave, changing the boot priority, even going into DOS and using "fdisk /mbr" on it and nothing gets me past the error.

I think it might be trying to load two instances of GRUB, but I'm not entirely sure.

---

### Post by meierfra on 2007-12-06
Did you try all the possible boot orders in the bios?  It does not only matter which drive you  boot from, but also which drive is second. Put  the  IDE drive in the last position.

If this did not solve the problem,  boot from the Ubuntu LiveCD (with the IDE drive connected) and post the output of

```
sudo fdisk -l
```

---

### Post by MyDearWatson on 2007-12-06
```
Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbff360c3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4212    33832858+  82  Linux swap / Solaris
/dev/hdb2   *        4213        4865     5245222+   7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab3c7715

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00060c2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33791   271426176    7  HPFS/NTFS
/dev/sdb2           33792       38913    41142465    f  W95 Ext'd (LBA)
/dev/sdb5           33792       38785    40114273+  83  Linux
/dev/sdb6           38786       38913     1028128+  82  Linux swap / Solaris

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe78176b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4864    39070048+   7  HPFS/NTFS
```

The Disk I need to get to is the first one.

---

### Post by meierfra on 2007-12-06
I'm not sure why you can't boot  ubuntu so I would like to see the file /boot/grub/menu.lst from you ubuntu partition. From the LiveCD:

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb5 /ubuntu
cat /ubuntu/boot/grub/menu.lst
```

Post the output.

Do you already have a plan how to access you NFTS/Swap partition ? I'm not sure, but it might be enough to change the type of the partition back to HPFS/NTFS:

```
sudo fdisk /dev/hdb
t
1
7
w

```

and  mount the partition

```
sudo mkdir Desktop/Windows
sudo mount -t ntfs /dev/hdb1 Desktop/Windows

```

If this worked you should be able to see your old files in the folder Windows on your Desktop.

If this did not work, I recommend testdisk (click on the link in my signature)

---

### Post by MyDearWatson on 2007-12-06
Well I semi-solved the problem.  I got access to the files I needed, but I still can't boot with the disk connected.  I can pretty much just throw away the drive now (though I most likely won't, me being the packrat I am...).  Thanks for your help!

---

### Post by meierfra on 2007-12-06
> I got access to the files I needed,

Just curious. Did you do it the way I suggested or some other way?

---

