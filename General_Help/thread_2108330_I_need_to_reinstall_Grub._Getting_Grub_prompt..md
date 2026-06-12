---
title: "I need to reinstall Grub. Getting Grub prompt."
date: 2013-01-24
forum: General Help
---

### Post by Shobuz99 on 2013-01-24
In a previous forum that was marked solved, I found a help link to the same problem I was having; which is, at dual boot, Grub does not run and stops at the Prompt "grub>"
Here's the link from that forum provided by staff emeritus drs305:
> "This post should help you restore your Grub installation:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10]("http://ubuntuforums.org/showthread.php?t=1014708")

Should work for Lucid as well for those reading this with a 10.04 install.
__________________
[GRUB2]("https://help.ubuntu.com/community/Grub2") 

Retired."
 
I tried the solution in the link provided, above.
I am still not able to go any further after I re-installed Grub to my /dev/sdb1 drive (Ubuntu-Linux 10.04)

My problem started when I tried to remotely copy/paste menu.lst into the Grub folder, using Windows XP (separate drive) through EXT2; when everything was working fine. 
Big mistake on my part.
When I shut down the machine and then started it up, It went to a black screen with some commands listed above the Grub prompt; which is grub>

I have a 10.04 Ubuntu CD which I booted to. I did not wish to install 10.04 all over again, because I thought I could fix the Grub. I'm just "trying" the 'Live' CD.
Incidentally, the Grub folder is now missing the menu.lst file and since I can't get to root on that drive, 
I can't just simply paste the file into the Grub folder; even though the drive is mounted and I can view ALL folders and files on the drive, I don't have permission.
It was setup to Dual Boot between HDDs and this has been working fine for 6 years. The Grub I had installed is the 1.98 version. 

Where should I go back to and what steps should I take. 
I'm in trouble here and need to resolve this quickly.

Thank you so much for your help.
Shobuz99

---

### Post by oldfred on 2013-01-24
You should install the grub2 boot loader to the MBR of the drive not to a partition or to sda not sda1 or sda2 etc.

With grub2 there is no menu.lst, that was with grub legacy (0.97). So unless your install is an upgrade from 9.04 or bedore you have grub2.

The manual procedures in drs305's thread will work. Most now in this:
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
    [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If you want a gui way, which only works now with grub2.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by iowabeakster on 2013-01-24
Boot onto your live CD.  Install this program as listed in the link (#2 option).

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")


Just do the "recommended repair".

Check back if it doesn't work.

--edit Old Fred a little quicker on the trigger--

---

### Post by Shobuz99 on 2013-01-24
> **oldfred said:**
> You should install the grub2 boot loader to the MBR of the drive not to a partition or to sda not sda1 or sda2 etc.

With grub2 there is no menu.lst, that was with grub legacy (0.97). So unless your install is an upgrade from 9.04 or bedore you have grub2.

The manual procedures in drs305's thread will work. Most now in this:
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
    [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If you want a gui way, which only works now with grub2.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Thank you. I tried the repair first and it stopped because
I have a 64bit system. Then I ran the "boot info"and it created a txt file.
Should I upload the text file here in full or can I attach the file here?
I want to make sure I follow the rules here, and I've forgotten the protocol for uploading txt files, etc.
thank you for your continued help.
Shobuz99

---

### Post by oldfred on 2013-01-24
Text file is large, forum may not even allow it.

But it should have given a link to a pastebin copy and you just need to post the link.

---

### Post by Shobuz99 on 2013-01-24
> **oldfred said:**
> Text file is large, forum may not even allow it.

But it should have given a link to a pastebin copy and you just need to post the link.

Pastebinit did not install here's the text file:

```

Drive: sda _____________________________________________________________________

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,857,264    39,857,202   7 NTFS / exFAT / HPF
S


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        60200DA2200D7FF0                       ntfs       
/dev/sdb1        8bb89afd-e18e-4e91-8a66-2394af41fb39   ext3       
/dev/sdb5        2c971fda-b03b-46a2-8df4-5fbdcdad5b68   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/8bb89afd-e18e-4e91-8a66-2394af41fb39 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/sdb1              ext3       (rw)

/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

[spybotsd]
timeout.old=30

--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2c971fda-b03b-46a2-8df4-5fbdcdad5b68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/fd0        /media/floppy0  auto,rw,user,noauto,exec 0       0
#/dev/fd0        /media/floppy0  auto,rw,user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto,umsdos,vfat,ext2 rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.867881298 = 3.079364096    boot/grub/core.img                             4
   2.751121044 = 2.953993728    boot/grub/stage2                               2
   2.530887127 = 2.717519360    boot/vmlinuz-2.6.32-44-generic                 2
  33.841781139 = 36.337335808   boot/vmlinuz-2.6.32-45-generic                 2
  33.841781139 = 36.337335808   vmlinuz                                        2
   2.530887127 = 2.717519360    vmlinuz.old                                    2
   2.539111614 = 2.726350336    boot/initrd.img-2.6.32-44-generic              5
   4.228259563 = 4.540059136    boot/initrd.img-2.6.32-45-generic             170
   4.228259563 = 4.540059136    initrd.img                                    170
   2.539111614 = 2.726350336    initrd.img.old                                 5


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-01-24__18h41 ===================
boot-repair version : 3.197~ppa27~lucid
boot-sav version : 3.197~ppa27~lucid
glade2script-gtk2 version : 3.2.2~ppa45~lucid
boot-sav-extra version :
boot-repair is executed in live-session (Ubuntu 10.04.1 LTS, lucid, Ubuntu, i686)
CPU op-mode(s):        64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

=================== os-prober:
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sdb1:Ubuntu 10.04.4 LTS (10.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="60200DA2200D7FF0" TYPE="ntfs"
/dev/sdb1: UUID="8bb89afd-e18e-4e91-8a66-2394af41fb39" TYPE="ext3"
/dev/sdb5: UUID="2c971fda-b03b-46a2-8df4-5fbdcdad5b68" TYPE="swap"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
================= /media/8bb89afd-e18e-4e91-8a66-2394af41fb39/etc/grub.d/ :
drwxr-xr-x  2 root root         4096 2012-01-25 16:28 grub.d
total 36
-rwxr-xr-x 1 root root 4444 2010-04-29 08:23 00_header
-rwxr-xr-x 1 root root 4843 2010-11-23 21:38 10_linux
-rwxr-xr-x 1 root root  918 2010-03-23 09:40 20_memtest86+
-rwxr-xr-x 1 root root 6605 2010-04-29 08:23 30_os-prober
-rwxr-xr-x 1 root root  214 2009-10-29 16:43 40_custom
-rw-r--r-- 1 root root  483 2009-10-29 16:43 README


No sdb1/etc/default/grub
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,  not-sepboot,    no-grubenv      nogrub, no-docgrub,     no-update-grub, 32,     no-boot,        is-os,  not--efi--part, part-has-no-fstab,      part-has-no-fstab,      ntldr,  no-winload,
     no-recov-nor-hid,       no-bmgr,        notwinboot,     nopakmgr,       nogrubinstall,  no---usr,       part-has-no-fstab,      not-sep-usr,    standard,       not-far,        /mnt/boot-sav/sda1.
sdb1    : sdb,  not-sepboot,    grubenv-ok      grub1,  grub1 , update-grub,    64,     with-boot,      is-os,  not--efi--part, fstab-without-boot,     fstab-without-efi,      no-nt,  no-winload,     no-recov-nor-hid,       no-bmgr,        notwinboot,     apt-get,        grub-install,   with--usr,      fstab-without-usr,      not-sep-usr,    standard,       not-far,        /media/8bb89afd-e18e-4e91-8a66-2394af41fb39.

sda     : not-GPT,      BIOSboot-not-needed,    has-no-EFIpart,         not-usb,        has-os, 63 sectors * 512 bytes
sdb     : not-GPT,      BIOSboot-not-needed,    has-no-EFIpart,         not-usb,        has-os, 63 sectors * 512 bytes


=================== parted -l:

Model: ATA QUANTUM FIREBALL (scsi)
Disk /dev/sda: 20.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  20.4GB  20.4GB  primary  ntfs         boot


Model: ATA ST380215A (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  76.7GB  76.7GB  primary   ext3            boot
2      76.7GB  80.0GB  3307MB  extended
5      76.7GB  80.0GB  3307MB  logical   linux-swap(v1)


^M                                                                          ^MWarning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
^M                                                                          ^MError: /dev/sr1: unrecognised disk label
================== parted -lm:

BYT;
/dev/sda:20.4GB:scsi:512:512:msdos:ATA QUANTUM FIREBALL;
1:32.3kB:20.4GB:20.4GB:ntfs::boot;

BYT;
/dev/sdb:80.0GB:scsi:512:512:msdos:ATA ST380215A;
1:32.3kB:76.7GB:76.7GB:ext3::boot;
2:76.7GB:80.0GB:3307MB:::;
5:76.7GB:80.0GB:3307MB:linux-swap(v1)::;

^M                                                                          ^MWarning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
^M                                                                          ^MError: /dev/sr1: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/8bb89afd-e18e-4e91-8a66-2394af41fb39 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/sdb1 type ext3 (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  adsp agpgart audio block bsg btrfs-control bus cdrom cdrom1 cdrw cdrw1 char console core cpu_dma_latency disk dmfm dmmidi dri dsp dvd dvd1 dvdrw dvdrw1 ecryptfs fb0 fd fd0 fd0u1040 fd0u1120 fd0u1440 fd0u1600 fd0u1680 fd0u1722 fd0u1743 fd0u1760 fd0u1840 fd0u1920 fd0u360 fd0u720 fd0u800 fd0u820 fd0u830 full fuse hpet input kmsg log lp0 mapper mcelog mem midi mixer net network_latency network_throughput null oldmem parport0 pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 scd1 sda sda1 sdb sdb1 sdb2 sdb5 sequencer sequencer2 sg0 sg1 sg2 sg3 shm snapshot snd sndstat sr0 sr1 stderr stdin stdout urandom usb usblp0 usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vga_arbiter zero
ls /dev/mapper:  control

================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  31 2c 60 02 00 00 00 00  |........1,`.....|
00000030  00 00 0c 00 00 00 00 00  c3 02 26 00 00 00 00 00  |..........&.....|
00000040  f6 00 00 00 01 00 00 00  f0 7f 0d 20 a2 0d 20 60  |........... .. `|
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

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    943M  121M  823M  13% /
none      devtmpfs    939M  304K  938M   1% /dev
/dev/sr1   iso9660    686M  686M     0 100% /cdrom
/dev/loop0
squashfs    658M  658M     0 100% /rofs
none         tmpfs    943M  276K  943M   1% /dev/shm
tmpfs        tmpfs    943M   76K  943M   1% /tmp
none         tmpfs    943M   96K  943M   1% /var/run
none         tmpfs    943M  4.0K  943M   1% /var/lock
none         tmpfs    943M     0  943M   0% /lib/init/rw
/dev/sdb1     ext3     71G   31G   38G  45% /media/8bb89afd-e18e-4e91-8a66-2394af41fb39
/dev/sdb1     ext3     71G   31G   38G  45% /media/sdb1
/dev/sda1  fuseblk     20G   17G  2.5G  88% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7b8b7b8

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2481    19928601    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96109610
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris


User choice: Is sdb (80.0GB) a removable disk? no
=================== Repair blockers
64bits detected. Please use this software in a 64bits session. (Please use Ubuntu-Secure-Remix-64bit (www.sourceforge.net/p/ubuntu-secured) which contains a 64bits-compatible version of this software.) This will enable this feature.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sdb (80.0GB) disk!

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages) and reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

No change has been performed on your computer. See you soon!
pastebinit  packages needed
E: Package pastebinit has no installation candidate
Could not install pastebinit
Please install the [pastebinit ] packages.  Then try again. 
```

I hope this is ok to put up. Thank you, oldfred

Shobuz99

---

### Post by oldfred on 2013-01-24
You did not post the beginning which shows the MBR's and what boot loader is installed where. 
You should just have Windows in sda and Ubuntu's grub2 boot loader in sdb.

Boot-Repair seems to be suggesting that or installing grub to both drives. But you need to be on line as Boot-Repair may need to download grub to correctly reconfigure. 

Did you boot a 64bit version to run Boot-Repair, it said 64 bit version detected. Maybe that is why the manual reinstalls are not working? Grub2 need to have same  version installed. If liveCD is not same version then a full chroot into system is required to download the correct version of grub.

---

### Post by Shobuz99 on 2013-01-24
> **oldfred said:**
> You did not post the beginning which shows the MBR's and what boot loader is installed where. 
You should just have Windows in sda and Ubuntu's grub2 boot loader in sdb.

Boot-Repair seems to be suggesting that or installing grub to both drives. But you need to be on line as Boot-Repair may need to download grub to correctly reconfigure. 

Did you boot a 64bit version to run Boot-Repair, it said 64 bit version detected. Maybe that is why the manual reinstalls are not working? Grub2 need to have same  version installed. If liveCD is not same version then a full chroot into system is required to download the correct version of grub.

ok. 
1) I had to copy the text and paste the boot-info_2013-01-24_18h41.txt
from the terminal output because it saved the file in the root of the Live CD. I could not access it. I obviously copied only 75% of the file.
Sorry about that.
2) Yes, I do have a 64 bit system. When the Boot-Repair ran, it told me that I needed to run the Ununtu-secure disk that has the 64 bit version
of boot-repair on it. The Live CD is a 32 bit version of 10.04 LTS I no longer have the 64 bit disk. I guess I need to download the ISO file and burn a copy and then use the boot-repair from that, correct?
3) How do I "full chroot into system is required to download the correct version of grub".?
What would be the correct Chroot commands?
4) Again, I had Grub version 1.98 installed on the Linux drive...not the Windows drive.

Sorry for the confusion. Thanks again for your help
Shobuz99

---

### Post by oldfred on 2013-01-24
If you chroot into your system it can down load the correct version from inside your system if on line. It then does not matter what you have booted with. 

Boot-Repair does not do the chroot (CHange ROOT) but I believe it will walk you thru the process.

       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by Shobuz99 on 2013-01-24
> **oldfred said:**
> If you chroot into your system it can down load the correct version from inside your system if on line. It then does not matter what you have booted with. 

Boot-Repair does not do the chroot (CHange ROOT) but I believe it will walk you thru the process.

       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Thank you. Before I read your above reply, I downloaded the boot-repair ISO file and burned it. I ran it, and am currently using it to log into this forum.
here is the file link generated by the repair boot-info option:
[http://paste2.org/2794617]("http://paste2.org/279461")
I hope this will help you
I decided to do this first, instead of running the repair.
Thank you for sticking with me.
Shobuz99

---

### Post by oldfred on 2013-01-24
Link still not correct. And that number at the standard Ubuntu paste location is someone else's.

I will not be back on line until tomorrow.

---

### Post by Shobuz99 on 2013-01-25
> **oldfred said:**
> Link still not correct. And that number at the standard Ubuntu paste location is someone else's.

I will not be back on line until tomorrow.

oldfred,
My apologies for the incorrect link. I discovered my error.
It should have been [http://paste2.org/p/2794617]("http://paste2.org/p/2794617")
I left out the /p directory in the link, previously.

I decided to run the actual Repair.
It turned out to be the right thing to do and has solved my problem.
I was able to recover and of course, now I am using Grub2
instead of the Grub Legacy 0.97-1.98 version. 
No more need for the menu.lst, as you had pointed out.

There is a new log file created for the repair,
if you care to look at it: [http://paste2.org/p/2796577]("http://paste2.org/p/2796577")

I am very happy that I burned the disk because now I 
have that Boot-Repair disk if something happens again.

I will mark this solved.

Thank you very much for all your persistent help.
I do appreciate it!

Shobuz99

---

### Post by oldfred on 2013-01-25
Glad it worked. :)

---

