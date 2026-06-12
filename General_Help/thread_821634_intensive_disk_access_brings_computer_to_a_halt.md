---
title: "intensive disk access brings computer to a halt"
date: 2008-06-07
forum: General Help
---

### Post by KhaaL on 2008-06-07
I'm having issues with my desktop computer a while back, when the disk starts to access files aggressively, for example when preload is working, the whole responsiveness of the computer comes to a near halt (the cursor stutters when I'm moving it, music playback stutters and general sluggishness). I don't know what causes this since I have 2 Gb RAM, AMD 5000+ X2 and the root partition resides on a raptor disk. I'm using hardy heron 64bit.

Help would be greatly appriciated.

---

### Post by happyhamster on 2008-06-07
Does your system have a swap partition? If so, when the system is unresponsive:

- is there swapping going on perhaps? (You can check with the System Monitor: System-->Administration-->System Monitor-->Resources.)
- how many ram is being used?
- are some processes (scrollkeeper or tracker perhaps) taking a lot of resources? (see System Monitor again, or run "top" in a terminal).

---

### Post by KhaaL on 2008-06-08
> **happyhamster said:**
> Does your system have a swap partition? If so, when the system is unresponsive:

- is there swapping going on perhaps? (You can check with the System Monitor: System-->Administration-->System Monitor-->Resources.)
- how many ram is being used?
- are some processes (scrollkeeper or tracker perhaps) taking a lot of resources? (see System Monitor again, or run "top" in a terminal).

Thanks for the tip, following it I could see a clear relation between the nasty lags and writing to swap (this happens when RAM reaches 90%+). So I guess the problem could be within the hdparm settings for the swap partition? How do I check that and what should the values be? I'm using SATA connections to my HDs.

---

### Post by Pjotr123 on 2008-06-08
Possibly this Firefox 3 bug:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)

---

### Post by KhaaL on 2008-06-09
> **Pjotr123 said:**
> Possibly this Firefox 3 bug:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)

Both nautilus and firefox can eat big chunks of my RAM, but this does not solve my problem since *any* large write to SWAP will make my system stutter...

---

### Post by happyhamster on 2008-06-09
- Just a wild guess, but could you show the output of: 

cat /etc/fstab

- And the output of:

sudo vol_id /dev/sda1
sudo vol_id /dev/sda2
sudo vol_id /dev/sda3
etc...

- where /dev/sda... are the partitions listed in fstab. The UUID's found should correspond to the ones in fstab. Be careful if you decide to edit fstab, because making an error could result in an unbootable system. (Make sure you have a live-cd ready for the rescue, for example.)

---

### Post by KhaaL on 2008-06-10
Here's the information you requested:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=24f83ad6-99a8-4c83-919c-5cf4cdf84f3a /               ext3    errors=remount-ro 0       1
# /dev/sdc2
UUID=1bbea7f0-2062-4e05-8362-492cd68b8740 /home           ext3    defaults        0       2
# /dev/sda1
UUID=3ED5E20743B012AC /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
#UUID=1fc76122-2dc6-42b5-97ca-8b08b390c1f8 /media/sda3     reiserfs    defaults        0       2
# /dev/sdb1
UUID=11475f8d-dbfd-43c7-bfc6-d1447724fa28 /media/sdb1     ext3    defaults        0       2
# /dev/sda5
UUID=b1142981-d368-48f2-9b36-8ae01ab0dc85 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```




**sudo vol_id /dev/sdc1**                         (06-10 10:12)
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=24f83ad6-99a8-4c83-919c-5cf4cdf84f3a
ID_FS_UUID_ENC=24f83ad6-99a8-4c83-919c-5cf4cdf84f3a
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


**sudo vol_id /dev/sdc2**                         (06-10 10:16)
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=1bbea7f0-2062-4e05-8362-492cd68b8740
ID_FS_UUID_ENC=1bbea7f0-2062-4e05-8362-492cd68b8740
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

**sudo vol_id /dev/sda1 **                        (06-10 10:30)
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=3ED5E20743B012AC
ID_FS_UUID_ENC=3ED5E20743B012AC
ID_FS_LABEL=dozey
ID_FS_LABEL_ENC=dozey
ID_FS_LABEL_SAFE=dozey

**sudo vol_id /dev/sda3 **                        (06-10 10:30)
ID_FS_USAGE=filesystem
ID_FS_TYPE=reiserfs
ID_FS_VERSION=3.6
ID_FS_UUID=ec536297-1a91-45fb-b4c7-f80c9ac25297
ID_FS_UUID_ENC=ec536297-1a91-45fb-b4c7-f80c9ac25297
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

** sudo vol_id /dev/sda5 **                        (06-10 10:30)
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=b1142981-d368-48f2-9b36-8ae01ab0dc85
ID_FS_UUID_ENC=b1142981-d368-48f2-9b36-8ae01ab0dc85
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

**sudo vol_id /dev/sdb1 **                        (06-10 10:30)
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=11475f8d-dbfd-43c7-bfc6-d1447724fa28
ID_FS_UUID_ENC=11475f8d-dbfd-43c7-bfc6-d1447724fa28
ID_FS_LABEL=ext3storage
ID_FS_LABEL_ENC=ext3storage
ID_FS_LABEL_SAFE=ext3storage

As you can see, they all have the correct UUIDs in fstab except for sda3 - which also is commented out fstab. I've also taken the output of fdisk -l in case it might be of any use:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3713    29824641    7  HPFS/NTFS
/dev/sda2           29490       30401     7325640    c  W95 FAT32 (LBA)
/dev/sda3            3714       28732   200965117+  83  Linux
/dev/sda4           28733       29489     6080602+   5  Extended
/dev/sda5           28733       29489     6080571   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x480b5154

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdda1dda1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2962        9039    48821535   83  Linux
/dev/sdc2             166        2961    22458870   83  Linux

Partition table entries are not in disk order

```

Thanks in advance for help.

---

