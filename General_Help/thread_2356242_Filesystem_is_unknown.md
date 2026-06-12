---
title: "Filesystem is unknown"
date: 2017-03-21
forum: General Help
---

### Post by n2222 on 2017-03-21
Hello, 
I have maybe the last version of Ubuntu (updated the last year), it's the only OS on my notebook. It worked with no problem, but once during a hang up I pressed Ctrl+Alt+Del (as I did in Windows); my notebook restarted with the following message:

error: unknown filesystem.
Entering rescue mode...
grub rescue> 

 then I run:

grub rescue> ls
(hd0) (hd0,msdos5) (hd0,msdos1) 

Then I run command: 

...> ls (hd0,...)   - for each of those partitions, and always got the same answer: 

Filesystem is unknown.
grub rescue> 

So what I have to do now?

---

### Post by ajgreeny on 2017-03-21
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by n2222 on 2017-07-31
Hello, I have this:

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


```
============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   969,058,303   969,056,256  83 Linux
/dev/sda2         969,060,350   976,771,071     7,710,722   5 Extended
/dev/sda5         969,060,352   976,771,071     7,710,720  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        5282410e-a41f-4baf-b474-ec4aaae7aeed   swap       
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       5e0e08f0-12bc-41ff-8de8-4b861bbba13e   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 31 16:25 ata-PIONEER_DVD-RW_DVRTD10RS_SGB1705760 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 31 16:26 ata-WDC_WD5000BPVT-22HXZT1_WD-WXE1E11HJZ89 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 31 16:25 ata-WDC_WD5000BPVT-22HXZT1_WD-WXE1E11HJZ89-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 31 16:25 ata-WDC_WD5000BPVT-22HXZT1_WD-WXE1E11HJZ89-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 31 16:25 ata-WDC_WD5000BPVT-22HXZT1_WD-WXE1E11HJZ89-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Jul 31 16:26 wwn-0x50014ee65687e2b9 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 31 16:25 wwn-0x50014ee65687e2b9-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 31 16:25 wwn-0x50014ee65687e2b9-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 31 16:25 wwn-0x50014ee65687e2b9-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/2795/mounts) leaked on lvs invocation. Parent PID 7423: bash
File descriptor 13 (/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules.cache) leaked on lvs invocation. Parent PID 7423: bash
File descriptor 63 (pipe:[27103]) leaked on lvs invocation. Parent PID 7423: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-07-31__16h26 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2795/mounts) leaked on lvs invocation. Parent PID 4596: /bin/sh
File descriptor 13 (/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules.cache) leaked on lvs invocation. Parent PID 4596: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="5282410e-a41f-4baf-b474-ec4aaae7aeed" TYPE="swap"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/zram0: UUID="5e0e08f0-12bc-41ff-8de8-4b861bbba13e" TYPE="swap"

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: ATA WDC WD5000BPVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  496GB  496GB   primary                   boot
2      496GB   500GB  3948MB  extended
5      496GB   500GB  3948MB  logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA WDC WD5000BPVT-2;
1:1049kB:496GB:496GB:::boot;
2:496GB:500GB:3948MB:::;
5:496GB:500GB:3948MB:linux-swap(v1)::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


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
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.8G  5.2M  1.8G   1% /
udev           devtmpfs   1.8G   12K  1.8G   1% /dev
tmpfs          tmpfs      363M  1.1M  362M   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.8G  8.0K  1.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.8G     0  1.8G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e00e0

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   969058303   484528128   83  Linux
/dev/sda2       969060350   976771071     3855361    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       969060352   976771071     3855360   82  Linux swap / Solaris


Error: no partitions


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by n2222 on 2017-08-03
the link is: [http://paste.ubuntu.com/25232025/](http://paste.ubuntu.com/25232025/)
So what have I do with this?

---

