---
title: "cannot boot, error reading sector"
date: 2016-04-18
forum: General Help
---

### Post by su-j on 2016-04-18
Hello,
Can someone help me with this please?

My computer wouldn't shut down, I got errors "blk_update_request i/o error dev sda sector xxxxxxx"
When trying te reboot after turning it off with the power button, I got "grub rescue unknown file system"

I did find some help here, but I don't really understand computers or systems too well so I got stuck at this point:
I managed to run boot repair via live usb and got this (which I have no idea what to do with):
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub.
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
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 2091728 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 32.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   966,766,591   966,764,544  83 Linux
/dev/sda2         966,768,638 1,000,214,527    33,445,890   5 Extended
/dev/sda5         966,768,640 1,000,214,527    33,445,888  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.5 GB, 15518924800 bytes
64 heads, 32 sectors/track, 14800 cylinders, total 30310400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    30,310,399    30,310,368   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       017fc117-c1ff-4a0d-abf4-73e6c8229866   ext3       
/dev/loop1                                              squashfs   
/dev/sda5        675abc98-b0b6-4724-b5d0-81836655efe2   swap       
/dev/sdb1        0C0D-367E                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 18 15:54 ata-LITE-ON_DVDRW_LH-20A1L -> ../../sr1
lrwxrwxrwx 1 root root  9 Apr 18 15:54 ata-LITE-ON_DVDRW_LH-20A1S -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 18 16:04 ata-PLEXTOR_PX-512M6Pro_P02450114163 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 18 15:54 ata-PLEXTOR_PX-512M6Pro_P02450114163-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 18 15:54 ata-PLEXTOR_PX-512M6Pro_P02450114163-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 18 15:54 ata-PLEXTOR_PX-512M6Pro_P02450114163-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Apr 18 16:04 usb-Intenso_Ultra_Line_13111800002031-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 18 15:54 usb-Intenso_Ultra_Line_13111800002031-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr 18 16:04 wwn-0x500230310036124a -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 18 15:54 wwn-0x500230310036124a-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 18 15:54 wwn-0x500230310036124a-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 18 15:54 wwn-0x500230310036124a-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1



=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda1: Input/output error
File descriptor 10 (/proc/16435/mounts) leaked on lvs invocation. Parent PID 21440: bash
File descriptor 63 (pipe:[64079]) leaked on lvs invocation. Parent PID 21440: bash
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-04-18__16h03 ===================
boot-repair version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
boot-repair is executed in live-session (Ubuntu 14.04.3 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
ls: cannot access /home/usr/.config: No such file or directory

=================== os-prober:


=================== blkid:
/dev/loop0: UUID="017fc117-c1ff-4a0d-abf4-73e6c8229866" TYPE="ext3"
/dev/loop1: TYPE="squashfs"
/dev/sda5: UUID="675abc98-b0b6-4724-b5d0-81836655efe2" TYPE="swap"
/dev/sdb1: UUID="0C0D-367E" TYPE="vfat"


=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: ATA PLEXTOR PX-512M6 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  495GB  495GB   primary                   boot
2      495GB   512GB  17.1GB  extended
5      495GB   512GB  17.1GB  logical   linux-swap(v1)


Model: Intenso Ultra Line (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  15.5GB  15.5GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:512GB:scsi:512:512:msdos:ATA PLEXTOR PX-512M6;
1:1049kB:495GB:495GB:::boot;
2:495GB:512GB:17.1GB:::;
5:495GB:512GB:17.1GB:linux-swap(v1)::;

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos:Intenso Ultra Line;
1:16.4kB:15.5GB:15.5GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk            477G
sda1  part            461G
sda2  part              1K
sda5  part swap        16G
sdb   disk           14.5G
sdb1  part vfat      14.5G
sr0   rom            1024M
sr1   rom            1024M
loop0 loop ext3         1G
loop1 loop squashfs 962.1M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0
sda2     0  0  0
sda5     0  0  0         [SWAP]
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
sr1      1  0  1 running
loop0    1  0  0
loop1    1  0  0         /rofs


=================== mount:
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop1 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 input kfd kmsg kvm log mapper mcelog mem memory_bandwidth net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/cow           overlay   976M  150M  776M  17% /
udev           devtmpfs  7.8G   12K  7.8G   1% /dev
tmpfs          tmpfs     1.6G  1.3M  1.6G   1% /run
/dev/sdb1      vfat       15G  2.0G   13G  14% /cdrom
/dev/loop1     squashfs  963M  963M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     7.8G  1.2M  7.8G   1% /tmp
none           tmpfs     5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     7.8G   76K  7.8G   1% /run/shm
none           tmpfs     100M   40K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00003f77

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   966766591   483382272   83  Linux
/dev/sda2       966768638  1000214527    16722945    5  Extended
/dev/sda5       966768640  1000214527    16722944   82  Linux swap / Solaris

Disk /dev/sdb: 15.5 GB, 15518924800 bytes
64 heads, 32 sectors/track, 14800 cylinders, total 30310400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3312

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    30310399    15155184    c  W95 FAT32 (LBA)


Error: no partitions


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

