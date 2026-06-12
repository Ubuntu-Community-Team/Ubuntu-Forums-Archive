---
title: "Partition Table Woes, Linux on HX4700 Woes"
date: 2007-09-11
forum: General Help
---

### Post by charr on 2007-09-11
I have been trying to install Familiar Linux on my HX4700 using my Feisty host computer, but seemed to have messed up real good in the process.

I have been following this [_guide_](http://www.handhelds.org/moin/moin.cgi/HpIpaqHx4700HowtoInstallLinux), but have had zero success in the area concerning the boot loader.  In [_another similar guide_](http://wservices.ch/~lucas/hx4700/) it makes mention of the fact that the boot loader needs to be copied to the entire drive, not a partition.  My SD Card, which is going to be used to load the boot loader, only allows me to use /dev/sdb1, not /dev/sdb.  I thought I might be able to copy it to /dev/sda, and then to /dev/sdb, but I was horribly wrong, and seemed to have messed up my partition table in the process.

**Command Used:**
```

sudo dd if=/home/shawn/Desktop/bootldr-1.2.5-hp.rom of=/dev/sda

```

Drive: Seagate Barracuda 7200.9 160GB
There is a boot partition, a swap partition, and a main partition.  Only about ~5GB of data is currently being store on the drive, and none of it is valuable.

Output of **fdisk -l**
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

```

GParted does not recognize the volume either.  Did my bootloader overwrite the parition table?  I am using the same machine with zero problems right now, is that normal as well?

Help on both problems is appreciated.

---

### Post by Sef on 2007-09-25
> GParted does not recognize the volume either. Did my bootloader overwrite the parition table? 

I would say yes.

This is my fdisk -l output:

```

Disk /dev/hda: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1094     8787523+  83  Linux
/dev/hda2            1095        2310     9767520   83  Linux
/dev/hda3            2311        2438     1028160   82  Linux swap / Solaris
```


> I am using the same machine with zero problems right now, is that normal as well?

Are you using a live cd or another hard drive?

---

