---
title: "Grub Rescue after partition deleted in Windows"
date: 2013-04-08
forum: General Help
---

### Post by jumbo2 on 2013-04-08
Hi All,

I have a Windows XP and a Ubuntu distribution installed on the same Hard Disk. Naturally, I would boot into Windows from a Ubuntu boot selection menu.

I had the following drives on the HD:
- C: about 80 GB
- D: about 60 GB
- E: non-formatted partition, about 100 GB
- Ubuntu partition, about 60 GB
- swap partition, about 8 GB

I decided to format partition E so I could use it, so I went into Computer Management under Windows and selected that partition and clicked on Delete Logical Drive. The result is that E + the ubuntu partition + the swap partition are now 1 unknown partition. It's like windows (that can't see linux installations) just grouped the last 3 partitions into 1, and it only took 1 second (I didn't format yet).

I immediately restarted the PC, I was shown an error: error: no such partition
with a grub rescue> prompt

To be able to boot back into Windows, I run the XP installation cd and fixed the boot and mbr.

Now I can boot into Windows, but I don't have a Ubuntu option anymore, and when I booted using the Ubuntu live CD, I ran the disk utility and even Ubuntu cannot see the last 2 partitions I had. The ubuntu partition was called /dev/sdb7, now the entire block (168 GB) shows up as /dev/sdb, while my first 2 partitions (windows) are still the same.

My Ubuntu partition has not been formatted. I know the installation is still there. I didn't know that deleting that unused, un-formatted partition would make such trouble. I should have done it under Ubuntu, not Windows. 

But what should I do now to be able to restore my Ubuntu partitions?

Thank you

---

### Post by bswilson on 2013-04-08
Have you tried to boot into Linux at all? Give this a shot from the [FONT=Courier New]grub>[/FONT] prompt:

[FONT=Courier New]rootnoverify (hd0,0)
makeactive
chainloader +1
boot[/FONT]

Press Enter after each of these four lines, and see if you can't get into Ubuntu. From there you can likely fix things via the **Disks** utility.

---

### Post by jumbo2 on 2013-04-09
> **bswilson said:**
> Have you tried to boot into Linux at all? Give this a shot from the [FONT=Courier New]grub>[/FONT] prompt:

[FONT=Courier New]rootnoverify (hd0,0)
makeactive
chainloader +1
boot[/FONT]

Press Enter after each of these four lines, and see if you can't get into Ubuntu. From there you can likely fix things via the **Disks** utility.

Thanks for replying.

Actually it was a "grub rescue" prompt... And I'm not getting it anymore since I fixed the MBR using the windows installation CD, so I'm booting directly into windows now.

BTW, I tried a few command at the grup rescue prompt: set root=(hd0,0) & makeactive. It would return that makeactive is an unknown command.

---

### Post by oldfred on 2013-04-09
I think those were grub legacy commands as with grub2 the first partition is hd0,1 and with grub legacy the first partition was hd0,0.

Windows often rewrites partition tables in strange ways when it sees an extended partition with unknown logical partitions. Best to use Windows tools only to shrink Windows NTFS partition and use Linux tools for everything else as they know the Linux partitions exist.

You may be able to manually boot, but use the commands here:
 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)


Or this is a gui that should fix grub or create a report that we can use to diagnose your problems.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by jumbo2 on 2013-06-04
> **oldfred said:**
> I think those were grub legacy commands as with grub2 the first partition is hd0,1 and with grub legacy the first partition was hd0,0.

Windows often rewrites partition tables in strange ways when it sees an extended partition with unknown logical partitions. Best to use Windows tools only to shrink Windows NTFS partition and use Linux tools for everything else as they know the Linux partitions exist.

You may be able to manually boot, but use the commands here:
 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)


Or this is a gui that should fix grub or create a report that we can use to diagnose your problems.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)


Hello Oldfred,

I'm sorry it took me some time to do the boot info you asked me to do. I had to finish with exams that I had first before getting back to solving my problem!

Here's the BootInfo log for my computer. Please be advised that I have 2 HDDs, and that the hard disk of interest is the sdb which has 320 GB. Please tell me if you think I can run the boot repair from ubuntu without risking to mess up my windows installation:



```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Windows 2000/XP/2003 is installed in the MBR of /dev/sda.
 => Windows 2000/XP/2003 is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 6271200 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the F:\syslinux 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   163,846,934   163,846,872   7 NTFS / exFAT / HPFS
/dev/sdb2         163,846,996   625,141,759   461,294,764   f W95 Extended (LBA)
/dev/sdb5         163,846,998   286,728,119   122,881,122   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4040 MB, 4040748544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,892,086     7,892,024   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       70cdf747-c6df-954a-990e-d588c6aa985a   ext2       
/dev/sda1        944CBEA34CBE7F92                       ntfs       New Volume
/dev/sdb1        5E7471B274718D91                       ntfs       
/dev/sdb5        0AD8880CD887F3EB                       ntfs       
/dev/sdc1        6CA1-07BB                              vfat       ADATA USB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/5E7471B274718D91  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/0AD8880CD887F3EB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  df 79 6b de d7 0f 2f 67  9c 05 24 b4 24 6e f3 6c  |.yk.../g..$.$n.l|
00000010  42 91 9a bf c9 8d be 93  9b 0a e9 ab fb 66 ed a9  |B............f..|
00000020  8e 9e 24 1b 26 b5 26 61  c1 4d 36 af 79 6c bc 8f  |..$.&.&a.M6.yl..|
00000030  99 a0 77 7a 4d 65 6c ae  00 cd 3a d1 82 17 d0 a6  |..wzMel...:.....|
00000040  ff 29 8e 1a 04 2c a7 1e  e7 a4 85 70 65 08 01 03  |.)...,.....pe...|
00000050  e5 27 3c 61 c2 19 69 03  de 35 57 33 6a 00 b5 5d  |.'<a..i..5W3j..]|
00000060  ce 57 81 70 d0 87 db bb  04 ad 8e 4e 3d 8d e0 87  |.W.p.......N=...|
00000070  75 74 66 87 ed 11 63 64  59 77 f6 a2 89 e2 e1 53  |utf...cdYw.....S|
00000080  62 f1 1b 59 93 be b6 64  1e b4 22 c6 27 17 1a 83  |b..Y...d..".'...|
00000090  0f 95 b7 bf 27 9f d0 42  62 0f 71 a5 bc b1 30 31  |....'..Bb.q...01|
000000a0  77 e1 da e5 a6 6c 5e e4  ed dd 3b 0f 1c 12 d9 f3  |w....l^...;.....|
000000b0  4e 46 c8 f2 03 87 11 a8  64 e2 61 be 2a 8e 73 47  |NF......d.a.*.sG|
000000c0  72 53 27 3e 1e 47 4f 73  93 dc 79 c1 92 5d ce 70  |rS'>.GOs..y..].p|
000000d0  aa 7e 25 3a ac fa 71 c8  b2 61 73 86 28 67 38 d1  |.~%:..q..as.(g8.|
000000e0  c1 11 dc 06 2c 69 b1 81  dc 36 23 0c dd 1c 3f 1e  |....,i...6#...?.|
000000f0  03 71 57 c9 f1 b2 22 51  48 42 e1 03 83 20 18 c1  |.qW..."QHB... ..|
00000100  2a db de a1 8a fb 6f f0  29 fc bc 6d c5 ea 44 e7  |*.....o.)..m..D.|
00000110  43 c0 93 e6 23 2e 02 8f  bc e4 e3 07 38 90 28 be  |C...#.......8.(.|
00000120  6c e4 6f 9c a6 96 46 4d  11 a0 35 f6 9d e3 6b 90  |l.o...FM..5...k.|
00000130  e4 8a b3 82 99 1c f4 06  70 4b 2c 9f 79 1e fa 78  |........pK,.y..x|
00000140  a6 c1 34 c2 38 f1 5f 3d  c2 e5 40 c4 47 c2 c3 86  |..4.8._=..@.G...|
00000150  4e 72 15 3a bd 0b 71 c1  49 b0 af a4 ce 5d d8 71  |Nr.:..q.I....].q|
00000160  32 66 74 58 b5 3e fa 42  14 dd 19 b3 46 d6 0f c8  |2ftX.>.B....F...|
00000170  09 9e a3 ba 43 68 5b b3  48 04 76 ad 55 5a 4a 0c  |....Ch[.H.v.UZJ.|
00000180  47 77 11 76 d5 2b 0e 4c  53 ff 1d 7c 78 a9 44 fc  |Gw.v.+.LS..|x.D.|
00000190  bb 6a be cc f7 a2 9a 05  69 f1 68 53 65 0b db 49  |.j......i.hSe..I|
000001a0  1a dd 30 0d e0 67 f9 e0  80 0c fa ed 36 d5 3c 55  |..0..g......6.<U|
000001b0  b9 cb 50 ad 79 92 39 1c  9c 01 47 13 93 9c 00 01  |..P.y.9...G.....|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 62 04 53 07 00 00  |..........b.S...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-06-03__10h54 ===================
boot-repair version : 3.198~ppa8~oneiric
boot-sav version : 3.198~ppa8~oneiric
glade2script version : 3.2.2~ppa45~oneiric
boot-sav-extra version : 3.198~ppa8~oneiric
boot-repair is executed in live-session (Ubuntu 11.10, oneiric, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=nodeadkeys locale=us_us  persistent noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash -- maybe-ubiquity
Unmount sda1 from /media/New Volume to avoid space incompatibilities

=================== os-prober:
/dev/sdb1:Microsoft Windows XP Professional:Windows:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="70cdf747-c6df-954a-990e-d588c6aa985a" TYPE="ext2"
/dev/sda1: LABEL="New Volume" UUID="944CBEA34CBE7F92" TYPE="ntfs"
/dev/sdb1: UUID="5E7471B274718D91" TYPE="ntfs"
/dev/sdb5: UUID="0AD8880CD887F3EB" TYPE="ntfs"
/dev/sdc1: LABEL="ADATA USB" UUID="6CA1-07BB" TYPE="vfat"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

XP not detected by os-prober on sdb5. Please report this message to [EMAIL="yannubuntu@gmail.com"]yannubuntu@gmail.com[/EMAIL]
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
gui-scan.sh: line 28: check_efi_dmesg: command not found

=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/5E7471B274718D91.
sdb5    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/0AD8880CD887F3EB.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    63 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST3160811AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  160GB  160GB  primary  ntfs         boot


Model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      32.3kB  83.9GB  83.9GB  primary   ntfs         boot
2      83.9GB  320GB   236GB   extended               lba
5      83.9GB  147GB   62.9GB  logical   ntfs


Model: ADATA USB Flash Drive (scsi)
Disk /dev/sdc: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  4041MB  4041MB  primary  fat32        boot



                                                                          
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.

                                                                          
Error: /dev/fd0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:160GB:scsi:512:512:msdos:ATA ST3160811AS;
1:32.3kB:160GB:160GB:ntfs::boot;

BYT;
/dev/sdb:320GB:scsi:512:512:msdos:ATA WDC WD3200AAKS-7;
1:32.3kB:83.9GB:83.9GB:ntfs::boot;
2:83.9GB:320GB:236GB:::lba;
5:83.9GB:147GB:62.9GB:ntfs::;

BYT;
/dev/sdc:4041MB:scsi:512:512:msdos:ADATA USB Flash Drive;
1:32.3kB:4041MB:4041MB:fat32::boot;


                                                                          
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.

                                                                          
Error: /dev/fd0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/5E7471B274718D91 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5 on /media/0AD8880CD887F3EB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd fd0 full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log lp0 mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb5 sdc sdc1 sdd sde sdf sdg sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 vga_arbiter zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  81 8a a1 12 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  a8 18 2a 01 00 00 00 00  |..........*.....|
00000040  f6 00 00 00 01 00 00 00  92 7f be 4c a3 be 4c 94  |...........L..L.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  d7 1a c4 09 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  ad 41 9c 00 00 00 00 00  |.........A......|
00000040  f6 00 00 00 01 00 00 00  91 8d 71 74 b2 71 74 5e  |..........qt.qt^|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  61 04 53 07 00 00 00 00  |........a.S.....|
00000030  00 00 0c 00 00 00 00 00  46 30 75 00 00 00 00 00  |........F0u.....|
00000040  f6 00 00 00 01 00 00 00  eb f3 87 d8 0c 88 d8 0a  |................|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    301M  120M  166M  42% /
udev      devtmpfs    1.5G   12K  1.5G   1% /dev
tmpfs        tmpfs    593M  856K  592M   1% /run
/dev/sdc1     vfat    3.8G  2.5G  1.4G  65% /cdrom
/dev/loop0
squashfs    668M  668M     0 100% /rofs
tmpfs        tmpfs    1.5G   12K  1.5G   1% /tmp
none         tmpfs    5.0M  4.0K  5.0M   1% /run/lock
none         tmpfs    1.5G  188K  1.5G   1% /run/shm
/dev/sdb1  fuseblk     79G   22G   57G  28% /media/5E7471B274718D91
/dev/sdb5  fuseblk     59G   46G   13G  79% /media/0AD8880CD887F3EB
/dev/sda1  fuseblk    150G   70G   80G  47% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16071606

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x42cd42cc

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   163846934    81923436    7  HPFS/NTFS/exFAT
/dev/sdb2       163846996   625141759   230647382    f  W95 Ext'd (LBA)
/dev/sdb5       163846998   286728119    61440561    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 4040 MB, 4040748544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x843a4aba

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7892086     3946012    b  W95 FAT32



=================== Default settings
Recommended-Repair
This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
pastebinit  packages needed
User refused to install pastebinit


```

---

### Post by oldfred on 2013-06-06
Your extended partition looks like it has space without anything shown. Often you can use testdisk to restore a missing partition. Then use Boot-Repair to install grub2's boot load to the MBR of sdb and set BIOS to boot sdb.

 [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Rebelli0us on 2013-06-06
OP: You may have accidentally deleted some of Grub's innards. A good geek can fix it in a minute, but I'd use "Grub Customizer". It has a simple GUI and will fix grub so it boots again.


FRED: haha, hëll yes it's vacation **every** day.

---

