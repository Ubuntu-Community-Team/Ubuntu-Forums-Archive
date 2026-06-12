---
title: "Boot trouble : Hard disk not detected ."
date: 2016-04-23
forum: General Help
---

### Post by nat7 on 2016-04-23
Hello everyone ! I come here today because yesterday my laptop on ubuntu 14.04 crashed ( Lenovo Ideapad Z710) for no apparent reason , and when I wanted to start it again , I only get the following error messages :

"EFI network 0 for IPV4 boot failed"
"EFI network 0 for IPV6 boot failed"

For precision I already presented my troubles on the french forums , and they  think the problem comes from the hardware , or from the hard disk firmware . I come here expecting you could think about something they didn't .

I'm actually on a live session , I tried using boot repair but they don't propose me the usual repair , all I can get is this boot info :

```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......SG|9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 3447296 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.5 GB, 15506341888 bytes
88 heads, 24 sectors/track, 14339 cylinders, total 30285824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    30,285,823    30,277,760   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        101C-E8DC                              vfat       STORE N GO
/dev/zram0       80d8daea-e6aa-44cc-bdc7-006f2e1495e2   swap       
/dev/zram1       96adb202-9d4d-4d3f-a562-84b609e3f644   swap       
/dev/zram2       3438c57b-0966-4d30-b4f6-d5979e6b64dc   swap       
/dev/zram3       6ca6008f-c748-43d2-a3c2-695ff24986e0   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 22 21:13 ata-MATSHITA_DVD-RAM_UJ8DB_11S0C19801ZVJ8210583 -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 22 21:13 usb-Multiple_Card_Reader_058F63666485-0:0 -> ../../sda
lrwxrwxrwx 1 root root  9 Apr 22 21:14 usb-Verbatim_STORE_N_GO_070B47B650F60179-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 22 21:13 usb-Verbatim_STORE_N_GO_070B47B650F60179-0:0-part1 -> ../../sdb1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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

menuentry "Boot-Repair-Disk session" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^64bit session (failsafe)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/1939/mounts) leaked on lvs invocation. Parent PID 7404: bash
File descriptor 63 (pipe:[24981]) leaked on lvs invocation. Parent PID 7404: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-04-22__21h14 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/1939/mounts) leaked on lvs invocation. Parent PID 4526: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sdb1: LABEL="STORE N GO" UUID="101C-E8DC" TYPE="vfat"
/dev/zram0: UUID="80d8daea-e6aa-44cc-bdc7-006f2e1495e2" TYPE="swap"
/dev/zram1: UUID="96adb202-9d4d-4d3f-a562-84b609e3f644" TYPE="swap"
/dev/zram2: UUID="3438c57b-0966-4d30-b4f6-d5979e6b64dc" TYPE="swap"
/dev/zram3: UUID="6ca6008f-c748-43d2-a3c2-695ff24986e0" TYPE="swap"


efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2001,2003,2002
Boot0000* EFI Network 0 for IPv4 (0C-54-A5-46-31-31) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(0c54a5463131,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0001* EFI Network 0 for IPv6 (0C-54-A5-46-31-31) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(0c54a5463131,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI USB Device (VerbatimSTORE N GO)	ACPI(a0341d0,0)PCI(1a,0)USB(0,0)USB(1,0)HD(1,1f80,1ce0080,101ce8dc)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to boot.repair@gmail.com
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  15.5GB  15.5GB  primary  fat32        boot, lba



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos:Verbatim STORE N GO;
1:4129kB:15.5GB:15.5GB:fat32::boot, lba;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G  5.2M  1.9G   1% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      388M  1.2M  387M   1% /run
/dev/sdb1      vfat        15G  652M   14G   5% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.9G  8.0K  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G     0  1.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sdb: 15.5 GB, 15506341888 bytes
88 heads, 24 sectors/track, 14339 cylinders, total 30285824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x101ce8dc

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    30285823    15138880    c  W95 FAT32 (LBA)


Error: no partitions


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

also here's some information from my BIOS :

```

Hard disk not detected
Sata Controller Mode AHCI

Secure boot disabled
(
platform mode user mode 
secure boot mode standard
) those two last lines don't appear when secure boot = enabled

Boot mode ( UEFI ) possibility of choosing legacy support.
OS optimize default [Other OS ] possibility of choosing Win 8 64 bits.
```

I must add that my computer came with windows 8 , I wanted to dual boot , I failed miserably by accidently deleting the windows 8 partition and ended up with only ubuntu 14.04 . 
That's the best I know , if you need complementary info or anything else ask . 

Thank you very much for everyone who took the time to read that and thank you +++ for those who will help me !

---

### Post by nat7 on 2016-04-23
[INDENT] 					Hello everyone ! I come here today because yesterday my laptop on  ubuntu 14.04 crashed ( Lenovo Ideapad Z710) for no apparent reason , and  when I wanted to start it again , I only get the following error  messages :

"EFI network 0 for IPV4 boot failed"
"EFI network 0 for IPV6 boot failed"

For precision I already presented my troubles on the french forums , and  they  think the problem comes from the hardware , or from the hard disk  firmware . I come here expecting you could think about something they  didn't .

I'm actually on a live session , I tried using boot repair but they  don't propose me the usual repair , all I can get is this boot info :

```


Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......SG|9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 3447296 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.5 GB, 15506341888 bytes
88 heads, 24 sectors/track, 14339 cylinders, total 30285824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    30,285,823    30,277,760   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        101C-E8DC                              vfat       STORE N GO
/dev/zram0       80d8daea-e6aa-44cc-bdc7-006f2e1495e2   swap       
/dev/zram1       96adb202-9d4d-4d3f-a562-84b609e3f644   swap       
/dev/zram2       3438c57b-0966-4d30-b4f6-d5979e6b64dc   swap       
/dev/zram3       6ca6008f-c748-43d2-a3c2-695ff24986e0   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 22 21:13 ata-MATSHITA_DVD-RAM_UJ8DB_11S0C19801ZVJ8210583 -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 22 21:13 usb-Multiple_Card_Reader_058F63666485-0:0 -> ../../sda
lrwxrwxrwx 1 root root  9 Apr 22 21:14 usb-Verbatim_STORE_N_GO_070B47B650F60179-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 22 21:13 usb-Verbatim_STORE_N_GO_070B47B650F60179-0:0-part1 -> ../../sdb1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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

menuentry "Boot-Repair-Disk session" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^64bit session (failsafe)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/1939/mounts) leaked on lvs invocation. Parent PID 7404: bash
File descriptor 63 (pipe:[24981]) leaked on lvs invocation. Parent PID 7404: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-04-22__21h14 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/1939/mounts) leaked on lvs invocation. Parent PID 4526: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sdb1: LABEL="STORE N GO" UUID="101C-E8DC" TYPE="vfat"
/dev/zram0: UUID="80d8daea-e6aa-44cc-bdc7-006f2e1495e2" TYPE="swap"
/dev/zram1: UUID="96adb202-9d4d-4d3f-a562-84b609e3f644" TYPE="swap"
/dev/zram2: UUID="3438c57b-0966-4d30-b4f6-d5979e6b64dc" TYPE="swap"
/dev/zram3: UUID="6ca6008f-c748-43d2-a3c2-695ff24986e0" TYPE="swap"


efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2001,2003,2002
Boot0000* EFI Network 0 for IPv4 (0C-54-A5-46-31-31) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(0c54a5463131,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0001* EFI Network 0 for IPv6 (0C-54-A5-46-31-31) 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(0c54a5463131,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI USB Device (VerbatimSTORE N GO)	ACPI(a0341d0,0)PCI(1a,0)USB(0,0)USB(1,0)HD(1,1f80,1ce0080,101ce8dc)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to boot.repair@gmail.com
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  15.5GB  15.5GB  primary  fat32        boot, lba



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos:Verbatim STORE N GO;
1:4129kB:15.5GB:15.5GB:fat32::boot, lba;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G  5.2M  1.9G   1% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      388M  1.2M  387M   1% /run
/dev/sdb1      vfat        15G  652M   14G   5% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.9G  8.0K  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G     0  1.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sdb: 15.5 GB, 15506341888 bytes
88 heads, 24 sectors/track, 14339 cylinders, total 30285824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x101ce8dc

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    30285823    15138880    c  W95 FAT32 (LBA)


Error: no partitions


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.


```

also here's some info coming from my BIOS
```


Hard disk not detected
Sata Controller Mode AHCI

Secure boot disabled
(
platform mode user mode 
secure boot mode standard
) those two last lines don't appear when secure boot = enabled

Boot mode ( UEFI ) possibility of choosing legacy support.
OS optimize default [Other OS ] possibility of choosing Win 8 64 bits.


```

I must add that my computer came with windows 8 , I wanted to dual boot ,
 I failed miserably by accidently deleting the windows 8 partition and 
ended up with only ubuntu 14.04 . 

That's the best I know , if you need complementary info or anything else ask . 



Thank you very much for everyone who took the time to read that and thank you +++ for those who will help me !

For admins : sorry for the double post , not knowing for sure the source of my problems I think posting here is better adapted than in the Hardware section .  



[/INDENT]

---

### Post by weatherman2 on 2016-04-23
Your hard drive has probably failed and needs to be replaced.  This is common - hard drives are somewhat unreliable.

---

### Post by nat7 on 2016-04-23
ok thanks for your reply , if it is dead , is there any "soft solution" (not implying professionnal help)  to get back some data from it ?

---

### Post by oldfred on 2016-04-23
Duplicate threads merged.
If you want an admin to move a thread you can just ask. Use the report post, it is not just for spam, but anything forum related.

Does UEFI/BIOS show drive? If no drive shown then no system will see it.

Can you check connections? Sometimes power or SATA cable comes loose.

---

### Post by nat7 on 2016-04-24
Hi thanks for the merging . I checked the connections yesterday , it seemed ok and I unplugged and plugged it again the right way  , I removed the dust carefully  , but it didn't work . Seems like the problem really comes from the hard drive itself ... :( .

> Does UEFI/BIOS show drive? 

Is there a difference between the two in term of accessing it ? that's really not my field so excuse my questions , but can you access one, or the other , or are they merged ? I mean when I start my computer by pressing alt+F2 I access what I think is the BIOS . Is UEFI something else ? 
Anyway , what I think is the BIOS , tells me no hard disk detected .

---

### Post by oldfred on 2016-04-24
UEFI is what has replaced BIOS on new systems. All systems with Widnows 8 or later have UEFI with secure boot turned on by default. But UEFI has CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
So now with UEFI there are settings/switches to turn on/off UEFI secure boot, UEFI and BIOS. Some also call it "Windows" or "other".

But is your f2 to get into UEFI/BIOS does not show a drive then either connections are bad. Or drive is dead.
You could try new cables, different computer, but not likely.
Do you get any clicking noises when it is powered up?

       If you are sure it will not start there are the old tricks which only sometimes work and if they do not, may damage drive even more so the very expensive methods may not work.
The old freezer trick to get drive cold and see if it will start. Or a tap with a rubber hammer. Both are to resolve the issue where the lubrication has dried up or failed and drive is sticking and motor is not strong enough to start it. If it gets going then it may start once.

---

### Post by nat7 on 2016-04-24
no clicking noises when it is powered up , actually the noise is exactly the same than it was or way too subtle in difference to be heard . When I have the occasion I shall try it on another computer just in case , would be nice if it was just the connections . If it''s not , well , nothing else to loose so I'll go for the old-school tricks you describe , seems fun .

Well thanks for everything , at this point I think all is said (especially when last solutions are including the use of a freezer :mrgreen:  ) , so I guess the Thread can be closed .

---

