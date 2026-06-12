---
title: "What did I do? Was running fine but no no boot &quot;error no such partition&quot;"
date: 2020-07-06
forum: General Help
---

### Post by Sour Mash on 2020-07-06
Well that went bad quickly! Everything was fine, I was salvaging files off an old hard disk, I'd got to the end everything was on the main disk, the one I was running Ubuntu from. I then wanted to format the old disk but it wouldn't, said it was in use. I figured I'd reboot and try again. Rebooted and I got 

error: no such partition.
Entering rescue mode...
grub rescue>

and the expectant blinky cursor.

I've pulled the old drive out and it is clean so I haven't got the wrong drive but I've rebooted the machine with just the one drive in it and still got the above.

I ran the repair disc and although it says its fixed a problem, it hasn't, I get the same error message. I have a clean and all my data in on a drive which I can't boot - any ideas before I start tearing stuff apart some more?? Repair disk gave me the following, I'm not sure what most if it means :-(

```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       -387940352 sectors.. But according to the info from 
                       the partition table, it has 3907026943 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 3,907,028,991 3,907,026,944   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B125-FDFE                              vfat       2TB2
/dev/sr0         2017-10-29-00-56-18-00                 iso9660    Boot-Repair-Disk 64bit
/dev/zram0       c8b89744-f7f4-4043-98a9-11a66886b3a0   swap       
/dev/zram1       29a1872f-c4c3-48b4-973e-e368c786216c   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul  6 16:14 ata-ST2000DM001-9YN164_Z1E1GZH7 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul  6 16:14 ata-ST2000DM001-9YN164_Z1E1GZH7-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Jul  6 16:11 ata-TSSTcorp_DVD+_-RW_TS-H653B -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul  6 16:11 usb-DELL_USB_HS-CF_Card_00000200C1A2-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 Jul  6 16:11 usb-DELL_USB_HS-MS_Card_00000200C1A2-0:2 -> ../../sdd
lrwxrwxrwx 1 root root  9 Jul  6 16:11 usb-DELL_USB_HS-SD_Card_00000200C1A2-0:3 -> ../../sde
lrwxrwxrwx 1 root root  9 Jul  6 16:11 usb-DELL_USB_HS-xD_SM_00000200C1A2-0:1 -> ../../sdc
lrwxrwxrwx 1 root root  9 Jul  6 16:14 wwn-0x5000c5004e7432bd -> ../../sda
lrwxrwxrwx 1 root root 10 Jul  6 16:14 wwn-0x5000c5004e7432bd-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


ADDITIONAL INFORMATION :
=================== log of boot-repair 20200706_1612 ===================
boot-repair version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr0.
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 1oct2017, zesty, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:


=================== blkid:
/dev/sda1: LABEL="2TB2" UUID="B125-FDFE" TYPE="vfat" PARTUUID="493e6a70-01"
/dev/sr0: UUID="2017-10-29-00-56-18-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="6b8b4567" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/zram0: UUID="c8b89744-f7f4-4043-98a9-11a66886b3a0" TYPE="swap"
/dev/zram1: UUID="29a1872f-c4c3-48b4-973e-e368c786216c" TYPE="swap"


=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda1.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	not-mmc, no-os,	2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:2000GB:scsi:512:4096:msdos:ATA ST2000DM001-9YN1:;
1:1049kB:2000GB:2000GB:fat32::lba;

BYT;
/dev/zram1:1035MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1035MB:1035MB:linux-swap(v1)::;

BYT;
/dev/sr0:742MB:scsi:2048:2048:unknown:TSSTcorp DVD+-RW TS-H653B:;

BYT;
/dev/zram0:1035MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1035MB:1035MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs 629.3M
sda   disk            1.8T
sda1  part vfat       1.8T 2TB2
sr0   rom  iso9660    708M Boot-Repair-Disk 64bit
zram0 disk            987M
zram1 disk            987M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sr0      1  0  1 running /cdrom
zram0    0  0  0         [SWAP]
zram1    0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1961224k,nr_inodes=490306,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=404280k,mode=755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12619)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=404276k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kfd kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdc sdd sde sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 40 40 00  |.X.mkfs.fat..@@.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 80 e0 e8 c0 46 07 00  00 00 00 00 02 00 00 00  |.....F..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 fe fd 25 b1 32  54 42 32 20 20 20 20 20  |..)..%.2TB2     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     395M  6.4M  389M   2% /run
/dev/sr0       iso9660   708M  708M     0 100% /cdrom
/dev/loop0     squashfs  630M  630M     0 100% /rofs
/cow           overlay   2.0G  5.2M  2.0G   1% /
tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.0G  4.0K  2.0G   1% /tmp
tmpfs          tmpfs     395M  4.0K  395M   1% /run/user/999
/dev/sda1      vfat      1.9T   32K  1.9T   1% /mnt/boot-sav/sda1

=================== fdisk -l:
Disk /dev/loop0: 629.3 MiB, 659873792 bytes, 1288816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x493e6a70

Device     Boot Start        End    Sectors  Size Id Type
/dev/sda1        2048 3907028991 3907026944  1.8T  c W95 FAT32 (LBA)


Disk /dev/zram0: 987 MiB, 1034948608 bytes, 252673 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 987 MiB, 1034948608 bytes, 252673 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


No OS or WinEFI system

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
The boot flag will be placed on sda1.


parted /dev/sda set 1 boot on
Information: You may need to update /etc/fstab.


                                                                          
Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by ActionParsnip on 2020-07-06
If you boot to the Ubuntu install media, can you see the internal drive's partitions and do they have files on them OK that you'd expect in an Ubuntu install?

---

### Post by Sour Mash on 2020-07-06
Do you mean boot with a live CD?

---

### Post by Sour Mash on 2020-07-06
OK so I booted into a Live CD of Ubuntu 20.04 (which is what was installed on the machine when it fell over).
I can see the disk in Disks, it shows an empty disc, as does the old one. No sign of any data - there were several hundred GBs of files on there and now it looks empty :-(

---

### Post by TheFu on 2020-07-06
> What did I do?
if i had to guess, I&#8217;d say you formatted the disk with the OS.

Do you have a backup?

---

### Post by Sour Mash on 2020-07-07
Hmm, well this is fun! No idea what I did but it's really done a number on the disk, Currently running TestDisk to see if I can recover some files but this is a steep learning curve. I think I deleted a partition but I can't understand how. Still, it doesn't matter how, just that it happened at the end of a massive successful session of getting all my old data off all my old drives into one place then BAM! Lost - boo hoo.

I must admit to having lost my love for Ubuntu, everything seems to difficult at every stage and you can easily wreck the whole thing with a careless click or command. That's hard to do on Windows.

I'll persevere but this feels overly complicated.

---

### Post by uninvolved on 2020-07-07
Pretty much everyone hoses a pile of data at one point. Everyone here (probably) has done similar.

The important thing is to use this as a learning experience. Learn good backup strategy and never again run commands/app options unless you know exactly what it is going to do.

---

### Post by TheFu on 2020-07-07
> **uninvolved said:**
> Pretty much everyone hoses a pile of data at one point. Everyone here (probably) has done similar

I've wiped disks.
I've had a failure on 1 disk wipe all the data because the file system was striped across 3 disks.
I've been hacked ... er ... a few times.  Got an MS-DOS boot-sector virus in the late 1980s and used a disk editor to wipe it from 50+ floppies, manually.

What each of these things did was teach a little lesson.  Eventually, I finally learned to have daily, automatic, versioned, backups.  I'm a little stupid, so that took about 10 yrs before just doing backups (1 copy) happened.  About 8 yrs after that, I finally learned that doing versioned backups was actually easier than doing 1-time backups and required very little more storage AND they were about 100x faster.

But everyone has to learn stuff in their own time, in their own way.

---

### Post by uninvolved on 2020-07-07
> **TheFu said:**
> But everyone has to learn stuff in their own time, in their own way.

I once cost my own company tens of thousands of dollars by losing data. That's not the worst. The worst was of little dollar value and was a bunch of personal files - including photographs.

These days, I use the 3-2-1 backup plan. I'm in my sixties and have been at this for a long time - I too took way too long to figure this out. My first loss of data would have been in the early 70s, an HP 9100B, and a magnetic strip card that I wiped with a magnet because I was an idiot teen in school. Storage today is cheap and easy. I haven't lost data in a long time, due to lots of painful lessons.

---

### Post by Sour Mash on 2020-07-10
Yeah, it's a lesson alright - most of this was not vital it was just that I thought I'd done all the consolidation and recovery work, had the guts of the machine on the floor and put it all back together only to kick myself in the crotch at the 11th hour! 
Never mind, I've salvaged the important things and the things I can't put back together I can find elsewhere with a bit of research and some torrent time.
I just now need to figure out why I can see the windows network on Ubuntu but I can't connect :-( And why I can't even see the Ubuntu machines on Windows! I can see everything on iOS and Android! Computers, don't you just love 'em?!?

---

### Post by TheFu on 2020-07-10
> **Sour Mash said:**
>  
I just now need to figure out why I can see the windows network on Ubuntu but I can't connect :-( And why I can't even see the Ubuntu machines on Windows! I can see everything on iOS and Android! Computers, don't you just love 'em?!?

Use ssh and sftp. Those problems will go away.  sftp is supported by every Linux file manager, just do:
```
sudo apt install ssh fail2ban
```
and setup name resolution or use avahi with {hostname}.local names.  Avahi is a desktop-only zeroconf protocol tool.

if you need help with getting CiFS between Windows and Linux working, be aware that both the Samba and Windows implementations changed the defaults this year for better security.  To my knowledge there isn't any point-n-click solution.  Editing some system config files is required.

---

### Post by XBMC old School on 2020-07-10
Sorry to snob but I don't. I unplug every drive accept the one I want to install too. That way it is idiot proof.

---

