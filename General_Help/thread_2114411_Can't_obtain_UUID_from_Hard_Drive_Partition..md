---
title: "Can't obtain UUID from Hard Drive Partition."
date: 2013-02-10
forum: General Help
---

### Post by gamerman56 on 2013-02-10
I just installed Ubuntu 12.10 32-bit and I am having some problems trying to get my Hard Drive's UUID.  I have tried manually mounting it and it works, but I have to use "-o dmask=000,fmask=111" as it is formatted as FAT32.

When I run "sudo fdisk -l" it come up with:

```

 
Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x0007eae6 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *        2048   965292031   482644992   83  Linux 
/dev/sda2       965294078   976771071     5738497    5  Extended 
Partition 2 does not start on physical sector boundary. 
/dev/sda5       965294080   976771071     5738496   82  Linux swap / Solaris 
 
Disk /dev/mapper/cryptswap1: 5876 MB, 5876219904 bytes 
255 heads, 63 sectors/track, 714 cylinders, total 11476992 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x8fc8a283 
 
Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table 
 
Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0xbd974a90 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *   903383145   976768064    36692460    c  W95 FAT32 (LBA) 
/dev/sdb2              64   903383144   451691540+   f  W95 Ext'd (LBA) 
/dev/sdb5             127   903383144   451691509    b  W95 FAT32 
 
Partition table entries are not in disk order
```My device is device has two partitions, "/dev/sdb1" and "/dev/sdb5".  "/dev/sdb1" is for my live USB installs and automounts perfectly.  "/dev/sdb5" is for storage but when will not automount.

When I try "sudo blkid"  only the first partition appears:

```
/dev/mapper/cryptswap1: UUID="5da4ac94-6b41-4135-813f-1fda34fadf32" TYPE="swap"  
/dev/sda1: UUID="a64e3e3f-bf23-4f8d-81b1-ef13d4d22ef7" TYPE="ext4"  
/dev/sdb1: LABEL="PENDRIVE" UUID="1C03-185E" TYPE="vfat" 
```Any help would be appreciated as this is my first day on Linux and I already love it way more than Windows.  If you need any more info, or help interpreting (still getting used to gnome) just ask, please!

---

### Post by linuxyogi on 2013-02-10
[http://www.iloveubuntu.net/how-repair-swap-partition-ubuntu](http://www.iloveubuntu.net/how-repair-swap-partition-ubuntu)

The the above link & see if you can obtain the UUID.

---

### Post by sudodus on 2013-02-10
Welcome to the Ubuntu Forums :-)

Try with this command, to see if it helps you find the UUID of the /dev/sdb5

```
sudo blkid -c /dev/null
```

The output about cryptswap is OK. This is because when you have 'encrypted home', also the swap will be encrypted.

But you should get information about all FAT32 partitions.

Another option is to install and run gparted

```
sudo apt-get install gparted
```
and run it with
```
gksudo gparted
```
Select device at the right top corner!
Click on the ***Partition*** pull down menu and select ***Information*** (or something similar, I don't have an English menu).

UUID should be shown there. If this does not work, there is 

- either something wrong with the partition table,

- or maybe the problem is that you run the newest version of Ubuntu (12.10). The previous version 12.04 LTS has long time support until April 2017, and it is more stable (debugged). If it will recognize your hardware, I'd recommend that you run 12.04 LTS, or at least that you test it live (booted from the install USB or CD drive).

---

### Post by gamerman56 on 2013-02-10
Thanks, I have obtained the UUID (I believe) from Gparted.  Under information it said "UUID: CCCD-6468".  My problem now when I run "sudo mount -a" is that Terminal says no special device exists.

```
$ sudo mount -a
mount: special device UUID=CCCD-6468 does not exist

```

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a64e3e3f-bf23-4f8d-81b1-ef13d4d22ef7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=bb7845d7-1966-460c-abf4-f6ba0a05faca none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
#/dev/hdb5
UUID=CCCD-6468 /media/uber/   vfat rw,user,auto,fmask=0177,dmask=0077,uid=1000   0  0
```

---

### Post by sudodus on 2013-02-10
> **gamerman56 said:**
> ...
UUID=CCCD-6468 /media/uber/   vfat rw,user,auto,fmask=0177,dmask=0077,uid=1000   0  0[/CODE]
I don't see any obvious error. I tried to mount a FAT32 drive with your specs (except I had another UUID and /mnt). It was possible with the following command, which should correspond to your line in fstab.

```
sudo mount -U D706-B2D6 -t vfat -o rw,user,auto,fmask=0177,dmask=0077,uid=1000 /mnt
```
The response was the following line in /etc/mtab
```
/dev/sdd1 /mnt vfat rw,noexec,nosuid,nodev,fmask=0177,dmask=0077,uid=1000 0 0
``` So 'the same' works for me.
--
Maybe there is a typing error.

- Double-check the UUID of your FAT32 partition.
- Double-check the directory /media/uber

It need not exist for automount, but when you mount via fstab or mount, it must exist, and have read/write access at least for root (superuser).

Maybe there is something wrong in the partition table or file system which also makes blkid fail to find the partition.

Can you try to check/repair your FAT32 file system with ```
chkdsk /f
``` when booted in Windows?

---

### Post by efflandt on 2013-02-10
Just curious what created sdb2 with sdb5 before sdb1 on your disk.  People with partitions in the wrong order often seem to have issues.

---

### Post by gamerman56 on 2013-02-10
> **efflandt said:**
> Just curious what created sdb2 with sdb5 before sdb1 on your disk.  People with partitions in the wrong order often seem to have issues.

I had Windows 7 before this, and so /dev/sdb5 was the original partition, but then I created another partition to use for my Live USB.


> **sudodus said:**
> It  was possible with the following command, which should correspond to your  line in fstab.

```
sudo mount -U D706-B2D6 -t vfat -o  rw,user,auto,fmask=0177,dmask=0077,uid=1000 /mnt
```The response was  the following line in /etc/mtab
```
/dev/sdd1 /mnt vfat rw,noexec,nosuid,nodev,fmask=0177,dmask=0077,uid=1000 0 0
``` So 'the same' works for me.
...

Can you try to check/repair your FAT32 file system with ```
chkdsk /f
``` when booted in Windows?

When try the command you gave I receive this:

```
$ sudo mount -U CCCD-6468 -t vfat -o rw,user,auto,fmask=0177,dmask=--77,uid=1000 /media/uber/
[sudo] password for mark: 
mount: no such partition found

```

While manually mounting the drive is still successful:

```
$ sudo mount /dev/sdb5 /media/uber

```

I will go boot up my Windows computer and get back to you with the results.

---

### Post by sudodus on 2013-02-10
> **gamerman56 said:**
> I had Windows 7 before this, and so /dev/sdb5 was the original partition, but then I created another partition to use for my Live USB.




When try the command you gave I receive this:

```
$ sudo mount -U CCCD-6468 -t vfat -o rw,user,auto,fmask=0177,dmask=--77,uid=1000 /media/uber/
[sudo] password for mark: 
mount: no such partition found

```

While manually mounting the drive is still successful:

```
$ sudo mount /dev/sdb5 /media/uber

```

I will go boot up my Windows computer and get back to you with the results.
Then I think that UUID is not CCCD-6468

Try this:

- Use [FONT="Courier New"]gksudo gparted[/FONT] again to put a label onto the partition /dev/sdb5: I suggest ***[COLOR="red"]uber[/COLOR]*** since you use that name for mounting.

- Mount by label instead (almost as safe as by UUID) and much better than mount by block device (/dev/sdb5 might change)

```
$ sudo mount [COLOR="Red"]-L uber[/COLOR] -t vfat -o rw,user,auto,fmask=0177,dmask=--77,uid=1000 /media/uber
```

and if that works enter it into /etc/fstab

```
#/dev/hdb5
[COLOR="red"]LABEL=uber[/COLOR] /media/uber/   vfat rw,user,auto,fmask=0177,dmask=0077,uid=1000   0  0
```

---

