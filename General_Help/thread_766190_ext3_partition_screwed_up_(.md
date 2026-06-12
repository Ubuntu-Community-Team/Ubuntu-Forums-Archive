---
title: "ext3 partition screwed up :("
date: 2008-04-25
forum: General Help
---

### Post by xpingux on 2008-04-25
So i need some help BADLY. i've got 5 hard drives in my linux box. it's set as a file server and each hard drive is full of data (i know i need some redundancy :( ). so one of the hard drives, named hdd1, is a 500 gig drive holding all of my music and a bunch of movies. i was using a windows program called fixtune to rename all the id3 tags of the mp3's until half way through it errored out and said that it couldn't see the drive anymore. so i checked the linux box and sure enough, i couldn't get into the drive either. so i restarted the box, and tried remounting the drive. it gave this error:

Cannot Mount Volume.
Unable to mount the volume
Details
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,  missing codepage or helper program, or other error  in some cases useful info is found in syslog -try  dmesg | tail or so

i'm too afraid to use fsck or e2fsck, since i don't want to LOSE the data at all. any suggestions would be very much appreciated. just so you guys already have it, i have my fdisk and dmesg | tail output below:

shhtephe@shhtephe-fileserver:~$ sudo fdisk -l
Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a77f3c8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       30401   244196001   83  Linux

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       60801   488384001   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?         410      119791   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x158aa0f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a9a8a9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4658    37415353+  83  Linux
/dev/sdc2            4659        4863     1646662+   5  Extended
/dev/sdc5            4659        4863     1646631   82  Linux swap / Solaris


shhtephe@shhtephe-fileserver:~$ dmesg | tail
[122456.050042] [drm] Initialized drm 1.1.0 20060810
[122456.066434] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[122456.066759] [drm] Initialized i915 1.6.0 20060119 on minor 0
[122456.068128] set status page addr 0x00033000
[122473.690791] UDF-fs: No VRS found
[122602.737482] kjournald starting.  Commit interval 5 seconds
[122602.737489] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[122602.748450] EXT3 FS on hdc1, internal journal
[122602.748460] EXT3-fs: mounted filesystem with ordered data mode.
[225813.097422] ext3: No journal on filesystem on hdd1


-- 
-Stephen Bailey 

p.s. if there's anything specific you'd like me to do, or run, let me know what it is, and i'll be sure to do it, and get back to this thread asap.


p.p.s. i sure hope all the hardy heron business doesn't take the steam out of my thread/question! :)

---

### Post by thehighhat on 2008-04-25
> **xpingux said:**
> So i need some help BADLY. i've got 5 hard drives in my linux box. it's set as a file server and each hard drive is full of data (i know i need some redundancy :( ). so one of the hard drives, named hdd1, is a 500 gig drive holding all of my music and a bunch of movies. i was using a windows program called fixtune to rename all the id3 tags of the mp3's until half way through it errored out and said that it couldn't see the drive anymore. so i checked the linux box and sure enough, i couldn't get into the drive either. so i restarted the box, and tried remounting the drive. it gave this error:

Cannot Mount Volume.
Unable to mount the volume
Details
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,  missing codepage or helper program, or other error  in some cases useful info is found in syslog -try  dmesg | tail or so

i'm too afraid to use fsck or e2fsck, since i don't want to LOSE the data at all. any suggestions would be very much appreciated. just so you guys already have it, i have my fdisk and dmesg | tail output below:

shhtephe@shhtephe-fileserver:~$ sudo fdisk -l
Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a77f3c8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       30401   244196001   83  Linux

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       60801   488384001   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?         410      119791   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x158aa0f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a9a8a9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4658    37415353+  83  Linux
/dev/sdc2            4659        4863     1646662+   5  Extended
/dev/sdc5            4659        4863     1646631   82  Linux swap / Solaris


shhtephe@shhtephe-fileserver:~$ dmesg | tail
[122456.050042] [drm] Initialized drm 1.1.0 20060810
[122456.066434] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[122456.066759] [drm] Initialized i915 1.6.0 20060119 on minor 0
[122456.068128] set status page addr 0x00033000
[122473.690791] UDF-fs: No VRS found
[122602.737482] kjournald starting.  Commit interval 5 seconds
[122602.737489] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[122602.748450] EXT3 FS on hdc1, internal journal
[122602.748460] EXT3-fs: mounted filesystem with ordered data mode.
[225813.097422] ext3: No journal on filesystem on hdd1


-- 
-Stephen Bailey 

p.s. if there's anything specific you'd like me to do, or run, let me know what it is, and i'll be sure to do it, and get back to this thread asap.


p.p.s. i sure hope all the hardy heron business doesn't take the steam out of my thread/question! :)



Just trying to understand....

How were you editing the files in Windows?  Over samba?  With a Windows program that mounts ext2/3?  


What does this show?  (man tune2fs for explanation)
  tune2fs -l /dev/hdd1

---

### Post by xpingux on 2008-04-25
Yes i have the linux box set up as a fileserver with samba. the drives are shared.all my other drives are running perfectly fine in the same environment.


i ran tune2fs, and got this:

```
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Permission denied while trying to open /dev/hdd1
Couldn't find valid filesystem superblock.

i then tried it with sudo and got a lot more: 

shhtephe@shhtephe-fileserver:~$ sudo tune2fs -l /dev/hdd1
[sudo] password for shhtephe:
tune2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          3b5faca6-f648-46ba-a8fc-4504ec35c8e2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              61063168
Block count:              122096000
Reserved block count:     6104800
Free blocks:              120129064
Free inodes:              61063157
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      994
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sun Sep 30 13:15:19 2007
Last mount time:          n/a
Last write time:          Thu Apr 17 17:39:17 2008
Mount count:              0
Maximum mount count:      34
Last checked:             Sun Sep 30 13:15:19 2007
Check interval:           15552000 (6 months)
Next check after:         Fri Mar 28 13:15:19 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Default directory hash:   tea
Directory Hash Seed:      94aca0af-394b-4bc3-a3e2-26f745b87656
Journal backup:           inode blocks
```

boy that's a lot. does this help at all?

---

### Post by chrisccoulson on 2008-04-25
This immediately jumps out:
```
Filesystem state:         not clean with errors
```
I'm afraid you're going to have to run fsck on this volume. Just make sure it is completely unmounted first (which will probably be the case, as you can't mount it anyway).

---

### Post by xpingux on 2008-04-25
well i'm seeing a ton of this:

Inode 5147898, i_size is 6444458803776527079, should be 0.  Fix<y>? yes

which makes me nervous because from what i know about hard drive file allocation, that means i'm deleting stuff.



am i wrong? is this doing good things to fix my file system?

---

### Post by chrisccoulson on 2008-04-25
Your filesystem is already broken, so I'm not sure what other choice you have to be honest

---

### Post by xpingux on 2008-04-26
so i cleaned the drive, and this is the new output of tunefs


```
shhtephe@shhtephe-fileserver:~$ sudo tune2fs -l /dev/hdd1
tune2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          3b5faca6-f648-46ba-a8fc-4504ec35c8e2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              61063168
Block count:              122096000
Reserved block count:     6104800
Free blocks:              11959694
Free inodes:              61052666
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      994
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sun Sep 30 13:15:19 2007
Last mount time:          n/a
Last write time:          Fri Apr 25 12:54:23 2008
Mount count:              0
Maximum mount count:      34
Last checked:             Fri Apr 25 12:54:23 2008
Check interval:           15552000 (6 months)
Next check after:         Wed Oct 22 12:54:23 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Default directory hash:   tea
Directory Hash Seed:      94aca0af-394b-4bc3-a3e2-26f745b87656
Journal backup:           inode blocks
```

as you can see, it's "clean" now. which might or might not be a good thing, since it still won't mount :S

so i dmesg | tail'd and here's the new output

shhtephe@shhtephe-fileserver:~$ dmesg | tail
[122602.737482] kjournald starting.  Commit interval 5 seconds
[122602.737489] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[122602.748450] EXT3 FS on hdc1, internal journal
[122602.748460] EXT3-fs: mounted filesystem with ordered data mode.
[225813.097422] ext3: No journal on filesystem on hdd1
[225901.442891] ext3: No journal on filesystem on hdd1
[348532.633932] ext3: No journal on filesystem on hdd1
[439217.233931] ext3: No journal on filesystem on hdd1
[439265.746406] ext3: No journal on filesystem on hdd1
[439733.201098] ext3: No journal on filesystem on hdd1

are we getting anywhere? :)

---

### Post by chrisccoulson on 2008-04-26
Try:
```
sudo tune2fs -j /dev/hdd1
```
...then try mounting it again

Out of interest, how are you mounting the drive? Is it using a line in your fstab? If so, could you post it here? what error do you get now when you try to mount?

---

### Post by xpingux on 2008-04-26
everything has been recovered.



i owe you a friggin coke, dude.



thanks a ton.

---

### Post by N2G(bn#7+ on 2008-05-05
Hi, I'm having a similar problem.

- Trying to mount /dev/sdb1 (which is a ext3 external hard drive partition, connected by firewire).
- Has always mounted with no problems in the past.
- Getting same error as above "Cannot mount volume..." etc.
- Rebooted with no success
- Have checked out [https://bugs.launchpad.net/ubuntu/+bug/226215](https://bugs.launchpad.net/ubuntu/+bug/226215) which is a similar issue, and posted a call for help there too
- ```
tune2fs -l
``` shows:
Last mounted on: <not available>
Filesystem state: clean
Last write time: Sun May 4 13:53:39 2008
...among other things
- ```
sudo tune2fs -j /dev/sdb1
``` gives the following:
tune2fs 1.40.8 (13-Mar-2008)
The filesystem already has a journal.

Is there a solution - the files are EXTREMELY important to me.

Thanks.

---

### Post by chrisccoulson on 2008-05-05
erlandh - The issue in this thread and the the issue in the bug report you linked to are completely unrelated. 'Cannot mount volume' is a very generic error and the inability to mount a volume could have one of many different causes.

The problem with the OP in this thread was that their EXT3 volume had errors. Your post already suggests that your ext3 volume is clean, so you don't have the same issue as the OP, and the steps I suggested to fix it won't work for you.

I also doubt that your issue is related to the issue in that bug report either. I don't think tune2fs would give you a good output if it was.

How are you mounting the volume? Is it being auto-mounted or is there a line in your /etc/fstab? Could you do the following in a terminal:
```
tail -f /var/log/syslog
```
Then connect your external hard-drive (you should see some messages come out on the terminal). Copy and paste those messages here.

---

### Post by N2G(bn#7+ on 2008-05-06
Thanks for your help and sorry, I wasn't aware they were unrelated.

Here's the output of your command:
```
May  7 07:44:32 Gibber-Gunyah kernel: [ 1392.810810] usb 4-4: new high speed USB device using ehci_hcd and address 4
May  7 07:44:32 Gibber-Gunyah NetworkManager: <debug> [1210110272.576388] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_0'). 
May  7 07:44:32 Gibber-Gunyah kernel: [ 1392.945136] usb 4-4: configuration #1 chosen from 1 choice
May  7 07:44:32 Gibber-Gunyah kernel: [ 1392.952519] scsi3 : SCSI emulation for USB Mass Storage devices
May  7 07:44:32 Gibber-Gunyah kernel: [ 1392.954172] usb-storage: device found at 4
May  7 07:44:32 Gibber-Gunyah kernel: [ 1392.954181] usb-storage: waiting for device to settle before scanning
May  7 07:44:32 Gibber-Gunyah NetworkManager: <debug> [1210110272.682408] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_0_if0'). 
May  7 07:44:32 Gibber-Gunyah NetworkManager: <debug> [1210110272.752306] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_0_usbraw'). 
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.945798] usb-storage: device scan complete
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.946683] scsi 3:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 0
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.949722] sd 3:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.950585] sd 3:0:0:0: [sdc] Write Protect is off
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.950590] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.950595] sd 3:0:0:0: [sdc] Assuming drive cache: write through
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.951584] sd 3:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.952453] sd 3:0:0:0: [sdc] Write Protect is off
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.952458] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.952461] sd 3:0:0:0: [sdc] Assuming drive cache: write through
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.952467]  sdc: sdc1 sdc2 sdc3
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.972551] sd 3:0:0:0: [sdc] Attached SCSI disk
May  7 07:44:37 Gibber-Gunyah kernel: [ 1397.972650] sd 3:0:0:0: Attached scsi generic sg4 type 0
May  7 07:44:37 Gibber-Gunyah NetworkManager: <debug> [1210110277.716294] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_0_if0_scsi_host'). 
May  7 07:44:37 Gibber-Gunyah NetworkManager: <debug> [1210110277.737121] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_0_if0_scsi_host_scsi_device_lun0'). 
May  7 07:44:37 Gibber-Gunyah NetworkManager: <debug> [1210110277.760469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_0_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May  7 07:44:38 Gibber-Gunyah NetworkManager: <debug> [1210110278.026685] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ST332062_0A_0_0_0'). 
May  7 07:44:38 Gibber-Gunyah NetworkManager: <debug> [1210110278.136524] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2436F04D50241F91'). 
May  7 07:44:38 Gibber-Gunyah NetworkManager: <debug> [1210110278.318910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a4b453a4_af39_42ed_9e08_ba7e076f6a2d'). 
May  7 07:44:38 Gibber-Gunyah NetworkManager: <debug> [1210110278.576726] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_60A0_7E59'). 
May  7 07:44:38 Gibber-Gunyah ntfs-3g[5885]: Version 1.913 
May  7 07:44:38 Gibber-Gunyah ntfs-3g[5885]: Mounted /dev/sdc3 (Read-Write, label "EHStorage3", NTFS 3.1) 
May  7 07:44:38 Gibber-Gunyah ntfs-3g[5885]: Cmdline options: rw,nosuid,nodev,locale=en_AU.UTF-8 
May  7 07:44:38 Gibber-Gunyah ntfs-3g[5885]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdc3,blkdev,blksize=4096 
May  7 07:44:38 Gibber-Gunyah hald: mounted /dev/sdc3 on behalf of uid 1000
May  7 07:44:38 Gibber-Gunyah kernel: [ 1399.337801] JBD: no valid journal superblock found
May  7 07:44:38 Gibber-Gunyah kernel: [ 1399.337818] EXT3-fs: error loading journal.
May  7 07:44:39 Gibber-Gunyah hald: mounted /dev/sdc2 on behalf of uid 1000
```

I guess the only relevant bit is "JBD: no valid journal superblock found"? I was originally mounting this on my laptop via firewire, but as you can see, I'm now mounting it via USB2.0 on my desktop pc. It's being auto-mounted when I turn it on, it's not in fstab.

---

### Post by N2G(bn#7+ on 2008-05-06
Also, the output of ```
fdisk -l /dev/sdc
``` is:
```
Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cfb07b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36954   296832973+  83  Linux
/dev/sdc2           36955       38259    10482412+   b  W95 FAT32
/dev/sdc3           38260       38913     5253255    7  HPFS/NTFS

```

Thanks.

---

### Post by N2G(bn#7+ on 2008-05-06
And output of mount:
```
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc3 on /media/EHStorage3 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc2 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

```

---

### Post by chrisccoulson on 2008-05-06
You said a few posts ago that you tried:
```
sudo tune2fs -j /dev/sdb1
```
...ad it output:
```
tune2fs 1.40.8 (13-Mar-2008)
The filesystem already has a journal.

```

Thats expected, because according to your output from mount, /dev/sdb1 is your root filesystem (not an external drive), which appears to be ok.

Are you sure it's not /dev/sdc1 that you're trying to mount?

Could you try
```
sudo fsck /dev/sdc1
```
on the unmounted volume

---

