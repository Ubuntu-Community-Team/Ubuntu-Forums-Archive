---
title: "Upgrade 16.04 to 18.04 , problem with partitions"
date: 2018-07-23
forum: General Help
---

### Post by ordak on 2018-07-23
Hi,

I had some sound , Thunderbird problems so I decided to upgrade from Ubuntu 16.04 to 18.04 . I was able to do it well but one problem has appeared for me. Like before I have three partitions, they are called /dev/sda1 ,  /dev/sda2 , /dev/sda3 .

Now it seems to me that   /dev/sda2 is no longer the partition to store kernels , it only contain the kernels for 16.04 . I suspect the kernels for 18.04 are stored somewhere else . My question is , how can I make /dev/sda2 the place for 18.04 kernels and not other places ?

---

### Post by ajgreeny on 2018-07-23
Kernels are not stored as you put it but are in the root partition, or possibly boot partition depending on your partition setup so I wonder if you now have two OSs on your machine, both 16.04 and 18.04.

With the system booted as normal please show us the output of command ```
mount
``` in terminal and then ```
sudo parted -l
``` which will give us a lot more info to deal with.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by ordak on 2018-07-24
> **ajgreeny said:**
> Kernels are not stored as you put it but are in the root partition, or possibly boot partition depending on your partition setup so I wonder if you now have two OSs on your machine, both 16.04 and 18.04.

With the system booted as normal please show us the output of command ```
mount
``` in terminal and then ```
sudo parted -l
``` which will give us a lot more info to deal with.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

**mount** command output :

```

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3989692k,nr_inodes=997423,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=804896k,mode=755)
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=40,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15496)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/var/lib/snapd/snaps/gnome-logs_37.snap on /snap/gnome-logs/37 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_36.snap on /snap/gnome-system-monitor/36 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_25.snap on /snap/gnome-logs/25 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_180.snap on /snap/gnome-calculator/180 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_51.snap on /snap/gnome-system-monitor/51 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_154.snap on /snap/gnome-calculator/154 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_69.snap on /snap/gnome-characters/69 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_4486.snap on /snap/core/4486 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_59.snap on /snap/gnome-3-26-1604/59 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_103.snap on /snap/gnome-characters/103 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_70.snap on /snap/gnome-3-26-1604/70 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_4917.snap on /snap/core/4917 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=804892k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)


```

**sudo parted -l** :

```

Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1050MB  512MB  ext2
 3      1050MB  1000GB  999GB                                     lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8468MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  8468MB  8468MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  991GB  991GB  ext4




```

---

### Post by ajgreeny on 2018-07-27
You have used LVM to install Ubuntu which is way beyond my ability to help, I'm afraid, so I will have to back out of this thread.
Do you remember whether 16.04 was also using LVM?

How did you upgrade from 16.04 to 18.04; clean install over 16.04 or using the online update process?

---

### Post by ordak on 2018-07-28
> **ajgreeny said:**
> You have used LVM to install Ubuntu which is way beyond my ability to help, I'm afraid, so I will have to back out of this thread.
Do you remember whether 16.04 was also using LVM?

I do not know about LVM, it (Ubuntu 16.04) was a fresh install on this laptop from DVD.

> 
How did you upgrade from 16.04 to 18.04; clean install over 16.04 or using the online update process?

You may take a look at this thread:

[https://ubuntuforums.org/showthread.php?t=2396463](https://ubuntuforums.org/showthread.php?t=2396463)

---

### Post by ajgreeny on 2018-07-28
OK, it was apparently a clean install over the 16.04, but you must have chosen LVM when you installed this new 18.04 version, and that is where, as I said, I have to bow-out of this problem as I know nothing about LVM or how to manage it and the partition setup when using it.

---

### Post by Dennis N on 2018-07-28
**sda2** was your boot partition. i don't see in your display that its mounted, so apparently not being used by 18.04. look for the kernels now in **/boot** of Ubuntu 18.04.

To have used **sda2** as boot partition in 18.04, you would have had to specify to mount it at **/boot** when installing.

---

### Post by ordak on 2018-07-30
> **Dennis N said:**
> **sda2** was your boot partition. i don't see in your display that its mounted, so apparently not being used by 18.04. look for the kernels now in **/boot** of Ubuntu 18.04.

To have used **sda2** as boot partition in 18.04, you would have had to specify to mount it at **/boot** when installing.

Can I use my "live installer" flash memory With Ubuntu 18.04.1 to reinstall OS, selecting **sda2** as my boot partition ? Any drawbacks ?

---

### Post by ordak on 2018-08-04
Bump.

---

### Post by Dennis N on 2018-08-05
> **ordak said:**
> Can I use my "live installer" flash memory With Ubuntu 18.04.1 to reinstall OS, selecting **sda2** as my boot partition ? Any drawbacks ?

Only drawback might be if you intend to install more than one operating system. You would need a different separate boot partition for each OS you have. 
Unless you are using an encrypted drive, you don't really need a separate boot partition anymore for Ubuntu - including LVM systems. But, if you need or just want one, when you reach 'installation type' screen during the installation process, choose the 'something else' option. This leads to the screen showing partitions. Select sda2, Click on 'change' just under the display, and fill in details, including where to mount it. There should be an option to mount at /boot. You need to pick the root LV also - those are listed at the top of the partitioning screen.

---

