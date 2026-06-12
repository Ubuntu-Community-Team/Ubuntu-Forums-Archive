---
title: "Ubuntu not booting"
date: 2014-08-23
forum: General Help
---

### Post by Hanjaya on 2014-08-23
I have an old Dell Dual Core Laptop that has only Ubuntu 14.04 OS installed. My kids was playing around with it couple days ago and for some reason, the laptop not booting. When I turned on the laptop, it showed me the GRUB command.

Then I tried to fix it with Boot Repair Disk, now when I turn on the laptop, it says:

"Windows could not start because the following file is missing or corrupt: \windows\SYSTEM32\CONFIG\SYSTEM ..."
Sorry for the long text but below is the generated Boot Info txt from Boot Repair Disk. Please help.
```

Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /WINDOWS/system32/drivers/ /q^|_'t`9.efi 
                       /bootmgr /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *    145,806,003   149,998,904     4,192,902   c W95 FAT32 (LBA)
/dev/sda2         149,508,094   156,301,311     6,793,218   5 Extended
/dev/sda5         149,508,096   156,301,311     6,793,216  82 Linux swap / Solaris

/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda5

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07D7-051E                              vfat       MEDIADIRECT
/dev/sda5        94686d8c-7690-44f7-ad72-428578388f56   swap       
/dev/sr0                                                iso9660    Boot-Repair-Disk 32bit

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
_IACK_SC(0) /* hack! */


/* 
 * The canonical non-remaped I/O and MEM addresses have these values
 * subtracted out.  This is arranged so that folks manipulating ISA
 * devices can use their familiar numbers and have them--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/6838/mounts) leaked on lvscan invocation. Parent PID 12460: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-08-22__07h58 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
File descriptor 8 (/proc/6838/mounts) leaked on lvs invocation. Parent PID 8218: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 32bit 24avr2013, raring, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda1:Windows NT/2000/XP (loader):Windows:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="MEDIADIRECT" UUID="07D7-051E" TYPE="vfat"
/dev/sda5: UUID="94686d8c-7690-44f7-ad72-428578388f56" TYPE="swap"
/dev/sr0: LABEL="Boot-Repair-Disk 32bit" TYPE="iso9660"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,  not-sepboot,    no-grubenv  nogrub, no-docgrub, no-update-grub, 32, no-boot,    is-os,  is-correct-EFI, part-has-no-fstab,  part-has-no-fstab,  ntldr,  no-winload, no-recov-nor-hid,   bootmgr,    notwinboot, nopakmgr,   nogrubinstall,  no---usr,   part-has-no-fstab,  not-sep-usr,    standard,   not-far,    /mnt/boot-sav/sda1.

sda : not-GPT,  BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os, 2048 sectors * 512 bytes


=================== parted -l:



Error: Can't have overlapping partitions.



Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label

=================== parted -lm:



Error: Can't have overlapping partitions.



Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


Error: /dev/sr0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd ecryptfs fb0 fd full fuse fw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 20 00  |.X.MSDOS5.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 b3 d2 b0 08  |........?.......|
00000020  86 fa 3f 00 fd 0f 00 00  00 00 00 00 02 00 00 00  |..?.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1e 05 d7 07 44  65 6c 6c 4d 44 33 70 6c  |..)....DellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 4e 54  |..............NT|
000001b0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 ff 0d  |LDR is missing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 ac bf cc 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.6G   21M  1.6G   2% /
udev           devtmpfs   1.6G   12K  1.6G   1% /dev
tmpfs          tmpfs      328M  752K  327M   1% /run
/dev/sr0       iso9660    496M  496M     0 100% /cdrom
/dev/loop0     squashfs   431M  431M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.6G  8.0K  1.6G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.6G     0  1.6G   0% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user
/dev/sda1      vfat       2.0G  1.3G  722M  65% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000909a4

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   145806003   149998904     2096451    c  W95 FAT32 (LBA)
/dev/sda2       149508094   156301311     3396609    5  Extended
/dev/sda5       149508096   156301311     3396608   82  Linux swap / Solaris



=================== Recommended repair
Recommended-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by alias2234 on 2014-08-23
> **Hanjaya said:**
> I have an old Dell Dual Core Laptop that has only Ubuntu 14.04 OS installed.

Hi
Don't worry, we are going to fix this problem.  :wink:

Have you tryied to do reboot, because it says that Boot is successfully repaired ???                 

I think you have to erase every trace of the old windows and format the hole hdd.
You have to do a fresh install with a Ubuntu live install DVD or USB stick.
Do you have ubuntu on a usb stick or dvd ?
Pls don't use the "Boot Repair Disk".

Only use ubuntu live dvd or live usb stick to do a fresh install with ubuntu.

When the desktop loads, click the Install button, and follow along,  then, at stage 4, select "Erase disk and install  Ubuntu".
That should take care of wiping the harddrive out completely.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by yancek on 2014-08-23
You have the syslinux bootloader installed to the master boot record of your only hard drive, sda.  Syslinux is usually used on CD/DVD/ or bootable flash drives.  Ubuntu uses a bootloader named GRUB.  Your first partition is a windows partition and shows windows files on it.  The only sign that a Linux system was ever present is the swap partition so your Ubuntu is gone.  No boot files, not system files and no data from your Linux.  Interestingly, the partition shows windows xp with 'some' xp boot files but also shows it as a FAT32 partition and xp uses ntfs as a filesystem.  You need to do a complete reinstall of Ubuntu or some other system.

---

### Post by ajgreeny on 2014-08-23
Can we just ask if this was originally a wubi installation?  Did you install Ubuntu within a running windows OS or did you repartition, or shrink the windows partition to make space for Ubuntu?

---

### Post by yancek on 2014-08-23
> Can we just ask if this was originally a wubi installation?

Didn't think about that.  However, every bootinfoscript output file I have seen with a wubi install showed some wubi boot file as an entry in the Boot Files section.  I think it's at least unusual that it is FAT32 since windows has used ntfs since W2K.

---

### Post by Hanjaya on 2014-08-23
It's an old laptop that ran windows xp previously, then I remember I completely wiped the xp and installed Ubuntu from DVD. I have the ubuntu 14 DVD but I don't want to fresh re install ubuntu, I would like to recover my computer because I have all my kid photos inside the laptop. Please help, thanks a lot.

---

### Post by LostFarmer on 2014-08-23
I would recommend the use of 'testdisk'.  READ:[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) step by step on recovery of lost partitions and other documents.
It looks like partitions were deleted.  Your first partition starts at sector 145806003 , no were near of the start of hdd.

---

