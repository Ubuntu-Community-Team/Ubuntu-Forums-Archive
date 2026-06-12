---
title: "Dual boot"
date: 2013-04-17
forum: General Help
---

### Post by ganten7 on 2013-04-17
[COLOR=#000000]I have been dual-booting ubuntu 12.10 alongside windows 7. Recently, ubuntu froze for no apparent reason. I turned the computer off and turned it back on. Neither windows or ubuntu worked. I had to emercency wipe windows and fixed it, but whenever I started ubuntu, I just got the screen you see here [/COLOR][https://www.dropbox.com/s/tu4jvtlf10...2021.55.58.jpg]("https://www.dropbox.com/s/tu4jvtlf10mul6c/2013-04-15%2021.55.58.jpg")[COLOR=#000000]. I don't know what to do and I really want ubuntu back. Somebody help me arrrgh![/COLOR]

---

### Post by papibe on 2013-04-17
Hi ganten7.

Take a look at [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). 

Regards.

---

### Post by ganten7 on 2013-04-17
a

---

### Post by ganten7 on 2013-04-17
Okay thank you so much!

---

### Post by ganten7 on 2013-04-17
I tried boot-repair but to no success. ;( Is there a command I can put into the program it automatically boots into to load the kernel?

---

### Post by papibe on 2013-04-17
Check your manuals or online documentation of your computer brand and model.

You need to find out what is the key or combination of keys that let's you get into the boot manager (either UEFI or BIOS), so you can select to boot from your USB stick.

As soon as you turn your computer, you should usually either keep it pressed, or press it repeatedly to get to the UEFI/BIOS menu.

The key 'F2' is a pretty common choice manufactures use.

Let us know how it goes.
Regards.

---

### Post by ganten7 on 2013-04-17
Okay so I changed the bios file and boot-repair booted and said it was done with repairs and to reboot. I did and it still takes me to the same screen. ;( Could it be problem with grub? Oh, and it states the error on the command line "cannot boot. you need to load the kernel first" whenever I put in the command "boot." Is there a way I could just type in a command that would load the kernel? Thanks.

---

### Post by Impavidus on 2013-04-18
Let Boot-Repair generate a BootInfo summary and post the link it gives you here.

---

### Post by ganten7 on 2013-04-18
I didn't make a url but this is what it says:

    Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info November 20th 2012]




============================= Boot Info Summary: ===============================


 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /wubildr


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........6.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 739904 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2             206,848    41,166,847    40,960,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     41,166,848   976,771,119   935,604,272   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 4005 MB, 4005560320 bytes
21 heads, 21 sectors/track, 17740 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          8,064     7,823,359     7,815,296   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sdb1        E289-3AB6                              vfat       STORE N GO


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb1        /live/image              vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)




================================ sda3/boot.ini: ================================


--------------------------------------------------------------------------------
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Windows" /noexecute=optin /fastdetect
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
append initrd=/ubninit boot=live config   quiet


label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 


label ubnentry1
menu label 32bits session
kernel /live/vmlinuz
append initrd=/live/initrd.img boot=live config   quiet


label ubnentry2
menu label 64bits session
kernel /live/vmlinuz2
append initrd=/live/initrd2.img boot=live config   quiet


label ubnentry3
menu label 32bits session (failsafe)
kernel /live/vmlinuz
append initrd=/live/initrd.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal


label ubnentry4
menu label 64bits session (failsafe)
kernel /live/vmlinuz2
append initrd=/live/initrd2.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal


label ubnentry5
menu label Memory test
kernel /live/memtest
append initrd=/ubninit 


--------------------------------------------------------------------------------


================= sdb1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1


============== sdb1: Version of COM32(R) files used by Syslinux: ===============


 menu.c32                           :  COM32R module (v4.xx)


=============================== StdErr Messages: ===============================


/mnt/BootInfo/sda3/ubuntu/disks/root.disk: Input/output error
Found Wubi on sda3. But could not create a loop device.
File descriptor 7 (pipe:[6715]) leaked on lvscan invocation. Parent PID 9660: bash
File descriptor 8 (pipe:[6715]) leaked on lvscan invocation. Parent PID 9660: bash
  No volume groups found
mdadm: No arrays found in config file or automatically


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-04-18__17h45 ===================
boot-repair version : 3.195~ppa11~lucid
boot-sav version : 3.195~ppa11~lucid
glade2script-gtk2 version : 3.2.2~ppa45~lucid
boot-sav-extra version : 3.195~ppa11~lucid
File descriptor 7 (pipe:[6715]) leaked on lvs invocation. Parent PID 3840: /bin/sh
File descriptor 8 (pipe:[6715]) leaked on lvs invocation. Parent PID 3840: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 29nov2012, squeeze, Debian, i686)
CPU op-mode(s):        32-bit, 64-bit
initrd=/ubninit boot=live config   quiet BOOT_IMAGE=/ubnkern


=================== os-prober:
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sda3:Windows 7 (loader):Windows1:chain


=================== blkid:
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLUTILITY" UUID="3030-3030" TYPE="vfat"
/dev/sda2: LABEL="Recovery" UUID="CC70378A703779F2" TYPE="ntfs"
/dev/sda3: LABEL="OS" UUID="AC7C4EC27C4E86D4" TYPE="ntfs"
/dev/sdb1: LABEL="STORE N GO" UUID="E289-3AB6" TYPE="vfat"
/dev/loop0: TYPE="squashfs"




1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.


There is Wubi inside sda3
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	ntldr,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.


sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes




=================== parted -l:


Model: ATA TOSHIBA MK5076GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  fat16        diag
2      106MB   21.1GB  21.0GB  primary  ntfs
3      21.1GB  500GB   479GB   primary  ntfs         boot




Backtrace has 16 calls on stack:
16: /lib/libparted.so.0(ped_assert+0x2a) [0xb7759dba]
15: /lib/libparted.so.0(+0x43ae7) [0xb7790ae7]
14: /lib/libparted.so.0(+0x44907) [0xb7791907]
13: /lib/libparted.so.0(+0x45bfc) [0xb7792bfc]
12: /lib/libparted.so.0(+0x11631) [0xb775e631]
11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xb7761ec2]
10: /lib/libparted.so.0(+0x47bb5) [0xb7794bb5]
9: /lib/libparted.so.0(+0x47dbf) [0xb7794dbf]
8: /lib/libparted.so.0(ped_disk_new+0x75) [0xb7762c95]
7: parted() [0x804e2f8]
6: parted() [0x804f3c3]
5: parted() [0x80516b2]
4: parted() [0x8052d21]
3: parted(main+0x2e) [0x8052e2e]
2: /lib/libc.so.6(__libc_start_main+0xe6) [0xb75aec76]
1: parted() [0x804c341]


                                                                          


You found a bug in GNU Parted! Here's what you have to do:


Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:


Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:


[http://ftp.gnu.org/gnu/parted/](http://ftp.gnu.org/gnu/parted/)


Please check this version prior to bug reporting.


If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:


[http://www.gnu.org/software/parted](http://www.gnu.org/software/parted)


for further information.


Your report should contain the version of this release (2.3)
along with the error message below, the output of


parted DEVICE unit co print unit s print


and the following history of commands you entered.
Also include any additional information about your setup you
consider important.


Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function
probe_partition_for_geom() failed.


=================== parted -lm:


BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA TOSHIBA MK5076GS;
1:1049kB:106MB:105MB:fat16::diag;
2:106MB:21.1GB:21.0GB:ntfs::;
3:21.1GB:500GB:479GB:ntfs::boot;


Backtrace has 16 calls on stack:
16: /lib/libparted.so.0(ped_assert+0x2a) [0xb767edba]
15: /lib/libparted.so.0(+0x43ae7) [0xb76b5ae7]
14: /lib/libparted.so.0(+0x44907) [0xb76b6907]
13: /lib/libparted.so.0(+0x45bfc) [0xb76b7bfc]
12: /lib/libparted.so.0(+0x11631) [0xb7683631]
11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xb7686ec2]
10: /lib/libparted.so.0(+0x47bb5) [0xb76b9bb5]
9: /lib/libparted.so.0(+0x47dbf) [0xb76b9dbf]
8: /lib/libparted.so.0(ped_disk_new+0x75) [0xb7687c95]
7: parted() [0x804e2f8]
6: parted() [0x804f3c3]
5: parted() [0x80516b2]
4: parted() [0x8052d21]
3: parted(main+0x2e) [0x8052e2e]
2: /lib/libc.so.6(__libc_start_main+0xe6) [0xb74d3c76]
1: parted() [0x804c341]


                                                                          


You found a bug in GNU Parted! Here's what you have to do:


Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:


Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:


[http://ftp.gnu.org/gnu/parted/](http://ftp.gnu.org/gnu/parted/)


Please check this version prior to bug reporting.


If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:


[http://www.gnu.org/software/parted](http://www.gnu.org/software/parted)


for further information.


Your report should contain the version of this release (2.3)
along with the error message below, the output of


parted DEVICE unit co print unit s print


and the following history of commands you entered.
Also include any additional information about your setup you
consider important.


Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function
probe_partition_for_geom() failed.




=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sdb1 on /live/image type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero
ls /dev/md:


=================== df -Th:


Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.5G  8.2M  1.5G   1% /
tmpfs        tmpfs    1.5G     0  1.5G   0% /lib/init/rw
udev         tmpfs    1.5G  200K  1.5G   1% /dev
tmpfs        tmpfs    1.5G     0  1.5G   0% /dev/shm
/dev/sdb1     vfat    3.8G  358M  3.4G  10% /live/image
tmpfs        tmpfs    1.5G  8.2M  1.5G   1% /live/cow
tmpfs        tmpfs    1.5G     0  1.5G   0% /live
tmpfs        tmpfs    1.5G  8.0K  1.5G   1% /tmp
/dev/sda1     vfat    100M  250K  100M   1% /mnt/boot-sav/sda1
/dev/sda2  fuseblk     20G  8.8G   11G  46% /mnt/boot-sav/sda2
/dev/sda3  fuseblk    447G   65G  382G  15% /mnt/boot-sav/sda3


=================== fdisk -l:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe1d96000


Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2563    20480000    7  HPFS/NTFS
/dev/sda3   *        2563       60802   467802136    7  HPFS/NTFS


Disk /dev/sdb: 4005 MB, 4005560320 bytes
21 heads, 21 sectors/track, 17740 cylinders
Units = cylinders of 441 * 512 = 225792 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          19       17741     3907648    c  W95 FAT32 (LBA)






=================== Default settings
Recommended-Repair
This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda3.
Additional repair would be performed: unhide-bootmenu-10s  repair-wubi fix-windows-boot


=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.






No change has been performed on your computer. See you soon!
pastebin.com ko (), using paste.ubuntu Please report this message to [email]yannubuntu@gmail.com[/email]

---

### Post by Impavidus on 2013-04-19
Something went wrong there, but it tells me you used wubi instead of a normal dual boot. This means Linux exists in a file in the Windows file system and indeed there is no Linux partition present on your hard disk. This makes installing and uninstalling Ubuntu easier, but any file system corruption in Windows breaks Ubuntu too. Fixing Windows may have damaged Ubuntu.

I assume Windows now works, right? Try to find a file called root.disk. It should be in the ubuntu/disks directory and it should be between 5 and 30 GB in size. Make a backup of that file. It contains the entire Ubuntu file system. I think the location of the file should have been mentioned in the summary, but it isn't, so I just hope it's still present somewhere. Next the easiest way is probably to reinstall Ubuntu (wubi or true dual boot, whatever you prefer) and recover your files from the backup of your root.disk.

If there is no root.disk your Ubuntu system is gone. You may try file recovery tools, but I hope you had backups of your important files.

---

### Post by ganten7 on 2013-04-19
I found the root.disk file, but it's 0 kilobytes. I backed it up though. It's fortunate that I didn't have ubuntu long enough to be putting important files on it so the file system isn't my biggest problem. So my best chance is to re-install then? How would I get rid of the previous partition for ubuntu that I made on my hard drive?(Sorry for all the questions. I really don't know anything about this)

---

