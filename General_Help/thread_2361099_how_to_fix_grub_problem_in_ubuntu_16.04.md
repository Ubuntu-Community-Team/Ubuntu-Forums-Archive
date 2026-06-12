---
title: "how to fix grub problem in ubuntu 16.04"
date: 2017-05-12
forum: General Help
---

### Post by offir on 2017-05-12
i have a computer with ubuntu 16.04 (only ubuntu)
I turn on the computer
And I have the following message

```
error: attempt to read or write outside of disk 'hd0'. 
Entering rescue mode... 
grub rescue>
```

i try to use boot Repair from a live cd of ubuntu 16.04 Without success

i try this link
[https://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error]("https://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error")
did not work

```
ls
```
give
```
(hd0) (hd0, msdos1) (hd0, msdos5)
```

i try this
```
sudo dpkg --configure -a
sudo apt-get install --reinstall linux-image-$(uname -r)
```
Also does not work
I get the same message

---

### Post by oldfred on 2017-05-12
What brand/model system. And what video card/chip?
UEFI or BIOS install?

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by offir on 2017-05-12
> What brand/model system. And what video card/chip?
UEFI or BIOS install?

Some details

Motherboard is [COLOR="#0000FF"]IBM Lenovo FRU 45R7727 Motherboard[/COLOR]
video card is [COLOR="#FF0000"]geforce 9400 gt[/COLOR]
Regular BIOS not UEFI



> you can run from Ubuntu live installer or any working install, use ppa version not ISO:
what is a ppa version


i try to make an online report but there is no link at the end

this is  a local report
```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

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
Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   304,197,631   304,195,584  83 Linux
/dev/sda2         304,199,678   312,580,095     8,380,418   5 Extended
/dev/sda5         304,199,680   312,580,095     8,380,416  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        91758232-da22-4adf-90c2-575ce63644c9   swap       
/dev/sr0         2017-02-15-21-44-13-00                 iso9660    Ubuntu 16.04.2 LTS amd64

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 May 12 16:50 ata-HL-DT-STDVD-ROM_GDRH20N -> ../../sr0
lrwxrwxrwx 1 root root  9 May 12 17:09 ata-ST3160812AS_41N3268_LEN_5LSEQGLW -> ../../sda
lrwxrwxrwx 1 root root 10 May 12 17:09 ata-ST3160812AS_41N3268_LEN_5LSEQGLW-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May 12 17:09 ata-ST3160812AS_41N3268_LEN_5LSEQGLW-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 May 12 17:09 ata-ST3160812AS_41N3268_LEN_5LSEQGLW-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/20442/mounts) leaked on lvs invocation. Parent PID 25384: bash
File descriptor 63 (pipe:[235117]) leaked on lvs invocation. Parent PID 25384: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-05-12__17h08 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
boot-info is executed in live-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:


=================== blkid:
/dev/sr0: UUID="2017-02-15-21-44-13-00" LABEL="Ubuntu 16.04.2 LTS amd64" TYPE="iso9660" PTUUID="15e2543d" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="91758232-da22-4adf-90c2-575ce63644c9" TYPE="swap" PARTUUID="d974441f-05"


=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: ATA ST3160812AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
1      1049kB  156GB  156GB   primary   ext4            boot
2      156GB   160GB  4291MB  extended
5      156GB   160GB  4291MB  logical   linux-swap(v1)


Model: HL-DT-ST DVD-ROM GDRH20N (scsi)
Disk /dev/sr0: 1554MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags:

Number  Start   End     Size    File system  Name   Flags
1      2048B   6143B   4096B                Apple
2      7389kB  9880kB  2490kB               EFI

=================== parted -lm:

BYT;
/dev/sda:160GB:scsi:512:512:msdos:ATA ST3160812AS:;
1:1049kB:156GB:156GB:ext4::boot;
2:156GB:160GB:4291MB:::;
5:156GB:160GB:4291MB:linux-swap(v1)::;

BYT;
/dev/sr0:1554MB:scsi:2048:2048:mac:HL-DT-ST DVD-ROM GDRH20N:;
1:2048B:6143B:4096B::Apple:;
2:7389kB:9880kB:2490kB::EFI:;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sr0   rom  iso9660    1.5G Ubuntu 16.04.2 LTS amd64
loop0 loop squashfs   1.4G
sda   disk          149.1G
sda2  part              1K
sda5  part swap         4G
sda1  part          145.1G

KNAME ROTA RO RM STATE   MOUNTPOINT
sr0      1  0  1 running /cdrom
loop0    1  1  0         /rofs
sda      1  0  0 running
sda2     1  0  0
sda5     1  0  0         [SWAP]
sda1     1  0  0


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2006760k,nr_inodes=501690,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=404472k,mode=755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=bb25b8603252c429)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=10633)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=404472k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri dvd ecryptfs fb0 fd full fuse gpiochip0 hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg lightnvm log lp0 mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.0G     0  2.0G   0% /dev
tmpfs          tmpfs     395M   12M  384M   3% /run
/dev/sr0       iso9660   1.5G  1.5G     0 100% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
aufs           aufs      2.0G  118M  1.9G   6% /
tmpfs          tmpfs     2.0G   19M  2.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.0G  424K  2.0G   1% /tmp
tmpfs          tmpfs     395M   76K  395M   1% /run/user/999

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd974441f

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 304197631 304195584 145.1G 83 Linux
/dev/sda2       304199678 312580095   8380418     4G  5 Extended
/dev/sda5       304199680 312580095   8380416     4G 82 Linux swap / Solaris


Error: no partitions
gui-tab-other.sh: line 93: _checkbutton_repairfilesystems: command not found


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.




```

---

### Post by offir on 2017-05-12
i try boot-repair
but it dont work 
see image

---

### Post by oldfred on 2017-05-12
When you run this command you are adding a ppa or private repository that is not part of Ubuntu's repository. Only use repositories you trust.
sudo add-apt-repository ppa

To see all the ext4 partitions
sudo parted -l
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by offir on 2017-05-13
> When you run this command you are adding a ppa or private repository that is not part of Ubuntu's repository. Only use repositories you trust.
sudo add-apt-repository ppa
ok but what ppa to add ?
```
sudo add-apt-repository ppa
```
just this line ?


> To see all the ext4 partitions
sudo parted -l
```
Model: ATA ST3160812AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  156GB  156GB   primary   ext4            boot
 2      156GB   160GB  4291MB  extended
 5      156GB   160GB  4291MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVD-ROM GDRH20N (scsi)                                    
Disk /dev/sr0: 1554MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      7389kB  9880kB  2490kB               EFI


```

> #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
i try this
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

```

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

and this 
```
sudo e2fsck -C0 -p -f -v /dev/sda
```
i got this
```
/dev/sda is in use.
e2fsck: Cannot continue, aborting.
```



> #if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1 

```
e2fsck 1.42.13 (17-May-2015)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```

```
sudo e2fsck -f -y -v /dev/sda
```
```
e2fsck 1.42.13 (17-May-2015)
/dev/sda is in use.
e2fsck: Cannot continue, aborting.

```

---

### Post by offir on 2017-05-13
When I try the commands that appear in the link from the first message

[https://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error]("https://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error")

```
grub rescue > ls
(hd0) (hd0, msdos9)
grub rescue > ls (hd0,msdos9)
grub rescue > ls (hd0,msdos8)
grub rescue > ls (hd0,msdos5) # suppose this is linux
grub rescue > ls (hd0,msdos5)
grub rescue > set root=(hd0,msdos5)
grub rescue > set prefix=(hd0,msdos5)/boot/grub
grub rescue > insmod normal
grub rescue > normal
```

in my case linux is on msdos5
when i Writing the line [COLOR="#FF0000"]insmod normal[/COLOR]
i get [COLOR="#FF0000"]Error: unknown filesystem[/COLOR]

---

### Post by offir on 2017-05-13
this is what i get from gparted
cant mount the partition

---

### Post by oldfred on 2017-05-13
It looks like gparted is automatically trying to run fsck and it also fails.
The ppa was Boot-Repair and details were in link in post #2 on copy & paste ppa into terminal to add Boot-Repair to live installer.

If fsck does not work, then severely damaged.
Best/easiest becomes reinstall and restore from your backup.

If you go into Disks and in upper right corned icon is Smart Status. It shows details on drive and can run drive tests. All I really know is whether drive is considered good or bad.

       sudo badblocks -v /dev/sda1 
    
 Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda1 


 Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

### Post by offir on 2017-05-27
I reinstalled the system with a new hard disk

The computer worked fine for a week and a half

And now this problem is back
I do not know what to do
I have already replaced a hard disk
What else could be

---

### Post by oldfred on 2017-05-27
If older computer it can be just about anything.
Power supply, mother board or even just cables to drive.

---

### Post by offir on 2017-05-28
Is there a way to know where the problem is ?

---

