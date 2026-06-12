---
title: "serious boot problem"
date: 2015-12-14
forum: General Help
---

### Post by ksundar1972 on 2015-12-14
Hi all,
I am a novice to Ubuntu
Here is a brief history of my system (Western Digital 500GB Hard disk with 4 primary partitions)
I first install windows 7 ultimate
Then installed ubuntu 14.04 LTS again i have upgraded with erase and install option to Ubuntu 15.10
After which somehow my booting corrupted and as a last resort i used latest Boot repair disk which also failed me
Below is my Boot-info generated online also see bin [http://paste.ubuntu.com/13987626](http://paste.ubuntu.com/13987626)
Kindly help me 


Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sr0                                                iso9660    Boot-Repair-Disk 32bit
/dev/zram0       80f2f13e-d36c-4c1d-aa8e-efa4173f2cee   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 9 Dec 14 14:32 ata-HL-DT-ST_DVDRAM_GH24NS70_K0021QN5753 -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/21373/mounts) leaked on lvs invocation. Parent PID 25294: bash
File descriptor 63 (pipe:[44040]) leaked on lvs invocation. Parent PID 25294: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2015-12-14__14h51 ===================
boot-info version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/21373/mounts) leaked on lvs invocation. Parent PID 22873: /bin/sh
No volume groups found
boot-info is executed in live-session (Boot-Repair-Disk 32bit 29nov2014, trusty, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 32bit" TYPE="iso9660"
/dev/zram0: UUID="80f2f13e-d36c-4c1d-aa8e-efa4173f2cee" TYPE="swap"

=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: /dev/sr0: unrecognised disk label

                                                                            Error: /dev/zram0: unrecognised disk label

=================== parted -lm:

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
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fd full fuse fw0 hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mei mem net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sg0 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.0G   44M  2.0G   3% /
udev           devtmpfs   2.0G   12K  2.0G   1% /dev
tmpfs          tmpfs      402M  1.2M  401M   1% /run
/dev/sr0       iso9660    599M  599M     0 100% /cdrom
/dev/loop0     squashfs   543M  543M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      2.0G  720K  2.0G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      2.0G     0  2.0G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user

=================== fdisk -l:



Error: no partitions
Error: no partitions


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the boot.


=================== User settings
The settings chosen by the user will not act on the boot.

---

### Post by grahammechanical on 2015-12-14
Here are a couple clues from the Boot Repair report

> no valid partition table found
Error: no partitions

Regards.

---

