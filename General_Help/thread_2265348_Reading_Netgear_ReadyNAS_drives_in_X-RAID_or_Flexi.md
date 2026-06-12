---
title: "Reading Netgear ReadyNAS drives in X-RAID or Flexi-RAID"
date: 2015-02-14
forum: General Help
---

### Post by Steve_Green on 2015-02-14
Hi all.

Ubuntu newbie, looking for some help if I may.

I have a SPARC-based Netgear ReadyNAS NV+ that has bitten the bullet. It was setup to use X-RAID (sometimes called Flexi-RAID). The 4x500GB drives had a 1.5TB useable space, with one drive as parity. I've connected all four drives via SATA connections to a PC, and ran Ubuntu Live CD 14.0.4 - I can see the drives using **fdisk -l** and if I run **disktypes** I get the following output:


```
--- /dev/sda
Block device, size 465.8 GiB (500107862016 bytes)
DOS/MBR partition map
Partition 1: 1.953 GiB (2097152000 bytes, 4096000 sectors from 32)
 Type 0xFD (Linux raid autodetect)
 Ext3 file system
   UUID 19D7E96B-46C0-4FA8-9C91-55AD62CA982F (DCE, v4)
   Volume size 1.953 GiB (2097086464 bytes, 127996 blocks of 16 KiB)
 Linux RAID disk, version 0.90.3
   RAID1 set using 4 regular 0 spare disks
   RAID set UUID FB039844-8B4F-B3AD-A7FE-C49905FF7DC3 (DCE, v11)
Partition 2: 512 MiB (536870912 bytes, 1048576 sectors from 4096032)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 748C5E1D-9F0A-26B1-3D4A-81EDFAC28E35 (NCS)
Partition 3: 463.3 GiB (497465450496 bytes, 971612208 sectors from
5144608)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 0C819D9F-4A65-09C7-52C4-8E407439F4FD (NCS)


--- /dev/sdb
Block device, size 465.8 GiB (500107862016 bytes)
DOS/MBR partition map
Partition 1: 1.953 GiB (2097152000 bytes, 4096000 sectors from 32)
 Type 0xFD (Linux raid autodetect)
 Ext3 file system
   UUID 19D7E96B-46C0-4FA8-9C91-55AD62CA982F (DCE, v4)
   Volume size 1.953 GiB (2097086464 bytes, 127996 blocks of 16 KiB)
 Linux RAID disk, version 0.90.3
   RAID1 set using 4 regular 0 spare disks
   RAID set UUID FB039844-8B4F-B3AD-A7FE-C49905FF7DC3 (DCE, v11)
Partition 2: 512 MiB (536870912 bytes, 1048576 sectors from 4096032)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 748C5E1D-9F0A-26B1-3D4A-81EDFAC28E35 (NCS)
 First 112 KiB are blank
Partition 3: 463.3 GiB (497465450496 bytes, 971612208 sectors from
5144608)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 0C819D9F-4A65-09C7-52C4-8E407439F4FD (NCS)


--- /dev/sdc
Block device, size 465.8 GiB (500107862016 bytes)
DOS/MBR partition map
Partition 1: 1.953 GiB (2097152000 bytes, 4096000 sectors from 32)
 Type 0xFD (Linux raid autodetect)
 Ext3 file system
   UUID 19D7E96B-46C0-4FA8-9C91-55AD62CA982F (DCE, v4)
   Volume size 1.953 GiB (2097086464 bytes, 127996 blocks of 16 KiB)
 Linux RAID disk, version 0.90.3
   RAID1 set using 4 regular 0 spare disks
   RAID set UUID FB039844-8B4F-B3AD-A7FE-C49905FF7DC3 (DCE, v11)
Partition 2: 512 MiB (536870912 bytes, 1048576 sectors from 4096032)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 748C5E1D-9F0A-26B1-3D4A-81EDFAC28E35 (NCS)
 First 112 KiB are blank
Partition 3: 463.3 GiB (497465450496 bytes, 971612208 sectors from
5144608)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 0C819D9F-4A65-09C7-52C4-8E407439F4FD (NCS)


--- /dev/sdd
Block device, size 465.8 GiB (500107862016 bytes)
DOS/MBR partition map
Partition 1: 1.953 GiB (2097152000 bytes, 4096000 sectors from 32)
 Type 0xFD (Linux raid autodetect)
 Ext3 file system
   UUID 19D7E96B-46C0-4FA8-9C91-55AD62CA982F (DCE, v4)
   Volume size 1.953 GiB (2097086464 bytes, 127996 blocks of 16 KiB)
 Linux RAID disk, version 0.90.3
   RAID1 set using 4 regular 0 spare disks
   RAID set UUID FB039844-8B4F-B3AD-A7FE-C49905FF7DC3 (DCE, v11)
Partition 2: 512 MiB (536870912 bytes, 1048576 sectors from 4096032)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 748C5E1D-9F0A-26B1-3D4A-81EDFAC28E35 (NCS)
Partition 3: 463.3 GiB (497465450496 bytes, 971612208 sectors from
5144608)
 Type 0xFD (Linux raid autodetect)
 Linux RAID disk, version 0.90.3
   RAID5 set using 4 regular 0 spare disks
   RAID set UUID 0C819D9F-4A65-09C7-52C4-8E407439F4FD (NCS)
 Linux LVM2 volume, version 001
   LABELONE label at sector 1
   PV UUID hN3fV6-VSQU-5vi3-gNCr-6ZkZ-OZoZ-EA6Z6y
   Volume size 1.357 TiB (1492395884544 bytes)
   Meta-data version 1
```
I've tried following the tutorial here: [http://home.bott.ca/webserver/?p=306](http://home.bott.ca/webserver/?p=306) but the **vgscan** step tells me that it found no volumes. I've also tried mounting the drives with no luck. Is anybody able to shed some light on how I get the data from these drives? Thanks.

---

### Post by steeldriver on 2015-02-14
Hello and welcome to the forums

I'm not familiar with the disktypes output, however afaik vgscan is specific to LVM volumes - for softraid (indicated by the 0xfd partition type), you probably need to install the mdadm package and then run

```

sudo mdadm --examine --scan

```

The other issue you may face is that the sparc-based NASes often use a large ext3 block size that prevents them from being mounted using regular Linux mount commands (although it may still be possible using fusefs)

---

### Post by Steve_Green on 2015-02-14
Thanks for the quick reply.

mdadm scan gives the following output:

```
ARRAY /dev/md0 UUID=449803fb:adb34f8b:99c4fea7:c37dff05
ARRAY /dev/md1 UUID=1d5e8c74:b1260a9f:ed814a3d:358ec2fa
ARRAY /dev/md2 UUID=9f9d810c:c709654a:408ec452:fdf43974
```

GParted shows this:

[[IMG]http://i357.photobucket.com/albums/oo11/euenahub/GParted.png[/IMG]]("http://s357.photobucket.com/user/euenahub/media/GParted.png.html")

I'm not sure how to use fusefs though? Any pointers?

---

### Post by steeldriver on 2015-02-14
Well I'm not a raid expert - you may want to wait for someone who is. However my next Q would be whether any of the arrays auto-assembled once you installed mdadm e.g.

```

sudo mdadm --detail /dev/md{0..2}

```

If not, the next thing to try would probably be to try to assemble them e.g. 

```

sudo mdadm --assemble /dev/md2

```
or
```

sudo mdadm --assemble --scan

```

Even if it doesn't succeed, the error(s) should be diagnostic

Let's not get into fusefs until you have an assembled array to work with and are able to see the filesystem

---

### Post by Steve_Green on 2015-02-14
Thanks again for your help.
```

root@ubuntu:/home/ubuntu# sudo mdadm --detail /dev/md{0..2}
mdadm: md device /dev/md0 does not appear to be active.
mdadm: md device /dev/md1 does not appear to be active.
mdadm: md device /dev/md2 does not appear to be active.

root@ubuntu:/home/ubuntu# sudo mdadm --assemble /dev/md2
mdadm: failed to add /dev/sdc3 to /dev/md2: Invalid argument
mdadm: failed to add /dev/sdb3 to /dev/md2: Invalid argument
mdadm: failed to add /dev/sda3 to /dev/md2: Invalid argument
mdadm: failed to add /dev/sdd3 to /dev/md2: Invalid argument
mdadm: failed to RUN_ARRAY /dev/md2: Invalid argument
root@ubuntu:/home/ubuntu# sudo mdadm --assemble /dev/md1
mdadm: failed to add /dev/sdc2 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdb2 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sda2 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdd2 to /dev/md1: Invalid argument
mdadm: failed to RUN_ARRAY /dev/md1: Invalid argument
root@ubuntu:/home/ubuntu# sudo mdadm --assemble /dev/md0
mdadm: failed to add /dev/sdc1 to /dev/md0: Invalid argument
mdadm: failed to add /dev/sdb1 to /dev/md0: Invalid argument
mdadm: failed to add /dev/sda1 to /dev/md0: Invalid argument
mdadm: failed to add /dev/sdd1 to /dev/md0: Invalid argument
mdadm: failed to RUN_ARRAY /dev/md0: Invalid argument
```

---

