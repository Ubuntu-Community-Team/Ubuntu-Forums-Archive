---
title: "error: out of disk at startup"
date: 2012-12-16
forum: General Help
---

### Post by mirzahadi on 2012-12-16
I have Ubuntu 11.04. I have been running it for more than a year now. All of a sudden this morning when I started the laptop, I got this error. I have employed plethora of methods to solve this issue but nothing has proved fruitful. 

I have tried to use all the suggested commands in Grub rescue. I have tried to use Live DVD to mount the hdd partition to re-install grub but it doesn't mount. I have tried to use UBCD, SuperGrub2, nothing.


Her is the boot-repair info:
```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info November 20th 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre7
    Boot sector info:  Syslinux looks at sector 61078 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   482,248,703   482,246,656  83 Linux
/dev/sda2         482,250,750   488,396,799     6,146,050   5 Extended
/dev/sda5         482,250,752   488,396,799     6,146,048  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16025387008 bytes
64 heads, 32 sectors/track, 15283 cylinders, total 31299584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,299,583    31,299,552   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        de6e9a79-9e70-439c-a266-f54e94b158a5   swap       
/dev/sdb1        0FE6-125F                              vfat       MULTIBOOT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda1: Input/output error
File descriptor 8 (/proc/3335/mounts) leaked on lvscan invocation. Parent PID 32608: bash
File descriptor 13 (/usr/share/icons/ubuntu-mono-dark/places/16/user-home.svg) leaked on lvscan invocation. Parent PID 32608: bash
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-12-16__06h30 ===================
boot-repair version : 3.195~ppa11~quantal
boot-sav version : 3.195~ppa11~quantal
glade2script version : 3.2.2~ppa45~quantal
boot-sav-extra version : 3.195~ppa11~quantal
boot-repair is executed in live-session (Ubuntu-Secure-Remix 12.10 29nov2012, quantal, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
cdrom-detect/try-usb=true noprompt boot=casper floppy.allowed_drive_mask=0 ignore_uuid live-media-path=/multiboot/edubuntu1210/casper/ initrd=/multiboot/edubuntu1210/casper/initrd.lz splash -- BOOT_IMAGE=/multiboot/edubuntu1210/casper/vmlinuz

=================== os-prober:
/dev/sdb1:Windows Recovery Environment (loader):Windows:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="de6e9a79-9e70-439c-a266-f54e94b158a5" TYPE="swap"
/dev/sdb1: LABEL="MULTIBOOT" UUID="0FE6-125F" TYPE="vfat"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

dir: cannot access /var/log/boot-sav/log/2012-12-16__06h30boot-repair34/sdb: No such file or directory
dir: cannot access /var/log/boot-sav/log/2012-12-16__06h30boot-repair34/sdb: No such file or directory
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  247GB  247GB   primary                   boot
2      247GB   250GB  3147MB  extended
5      247GB   250GB  3147MB  logical   linux-swap(v1)


Model: SSK SFD205 (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA Hitachi HTS54322;
1:1049kB:247GB:247GB:::boot;
2:247GB:250GB:3147MB:::;
5:247GB:250GB:3147MB:linux-swap(v1)::;

BYT;
/dev/sdb:16.0GB:scsi:512:512:msdos:SSK SFD205;
1:16.4kB:16.0GB:16.0GB:fat32::boot, lba;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/this/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=this)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  agpgart alarm ashmem autofs binder block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.5G   28M  1.5G   2% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      593M  836K  592M   1% /run
/dev/sdb1      vfat        15G  6.8G  8.2G  46% /cdrom
/dev/loop0     squashfs   723M  723M     0 100% /rofs
tmpfs          tmpfs      1.5G   12K  1.5G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.5G   76K  1.5G   1% /run/shm
none           tmpfs      100M   44K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087a54

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482248703   241123328   83  Linux
/dev/sda2       482250750   488396799     3073025    5  Extended
/dev/sda5       482250752   488396799     3073024   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16025387008 bytes
64 heads, 32 sectors/track, 15283 cylinders, total 31299584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee2cd

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31299583    15649776    c  W95 FAT32 (LBA)


No OS has been found on this computer.

=================== Recommended repair
Recommended-Repair
This setting will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by Impavidus on 2012-12-16
Before everyone has to extract this information from the rather verbose boot-repair info, could you tell what kind of installation this is (Ubuntu only, dual boot, wubi install inside windows)? I understand you can boot from a live DVD, but you're unable to mount the file system on the hard drive, which is somewhat strange.

You mentioned "out of disk". Having no more free disk space in your root partition can indeed be the cause of a boot failure. It can be caused by a partition that was too small or storing too much stuff on it (excessively large log files can be the cause too). Using gparted on your live DVD you may be able to make the partition larger. If you get it mounted you can investigate and delete some files.

Furthermore, 11.04 is end of live and has been unsupported for two months. You may want to upgrade to a more recent version. If you decide to do so now with a clean install, you won't have to solve your current problem entirely (although you may want to backup some files first).

---

### Post by oldfred on 2012-12-16
Script shows a full install with just one Linux partition and swap.

But script was not able to mount sda1, which means grub could not mount it.  I though Boot-Repair would try to run fsck, but do not see that it did.

Was system shutdown abnormally? Power failure or shutoff while running by power switch? That can cause file corruption and you need to run fsck from liveCD.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by mirzahadi on 2012-12-17
> #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1 	

Tried it but gives error. Thanks for your suggestion.

Eventually I had to extract my data through Testdisk. I wiped the hdd and installed the latest Ubuntu 12.10.

---

