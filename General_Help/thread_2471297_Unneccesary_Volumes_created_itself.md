---
title: "Unneccesary Volumes created itself"
date: 2022-01-26
forum: General Help
---

### Post by krishn7071 on 2022-01-26
[IMG]https://www.facebook.com/plugins/post.php?href=https%3A%2F%2Fwww.facebook.com%2Fkrishankumar89017%2Fposts%2F1289727981531963[/IMG][IMG]https://www.facebook.com/plugins/post.php?href=https%3A%2F%2Fwww.facebook.com%2Fkrishankumar89017%2Fposts%2F1289727981531963[/IMG]Unwanted Volumes created itself in my ubuntu 20.04 i dont know where it come from these are two volumes of 104 MB and 45 MB in /media/username/disk how to solve this issue and what is that actually

---

### Post by tea for one on 2022-01-26
> /media is intended as a mount point for external devices, such as hard drives or removable media (floppies, CDs, DVDs). 
More info here [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

Do you have USB sticks (or similar) attached?

---

### Post by krishn7071 on 2022-01-26
> **tea for one said:**
> More info here [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

Do you have USB sticks (or similar) attached?

sir no USB attached to my system and how can i remove these both....? is there any data loss....?

---

### Post by ActionParsnip on 2022-01-26
What is the output of:
```

sudo parted -l; mount; lsb_release -a; uname -a

```
Thanks

---

### Post by krishn7071 on 2022-01-28
Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  473MB   472MB   ntfs            Basic data partition          hidden, diag
 2      473MB   578MB   105MB   fat32           EFI system partition          boot, esp
 3      578MB   595MB   16.8MB                  Microsoft reserved partition  msftres
 4      595MB   157GB   156GB   ntfs            Basic data partition          msftdata
 8      157GB   620GB   464GB   ext4
 5      620GB   628GB   8112MB  linux-swap(v1)                                swap
 6      628GB   629GB   666MB   ntfs                                          hidden, diag
 7      629GB   1000GB  371GB   ntfs            Basic data partition          msftdata




sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=1920824k,nr_inodes=480206,mode=755,inode64)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=390848k,mode=755,inode64)
/dev/sda8 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k,inode64)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755,inode64)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/misc type cgroup (rw,nosuid,nodev,noexec,relatime,misc)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=18907)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/heroku_4078.snap on /snap/heroku/4078 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/curl_623.snap on /snap/curl/623 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/canonical-livepatch_126.snap on /snap/canonical-livepatch/126 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/flutter_111.snap on /snap/flutter/111 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/whatsapp-for-linux_31.snap on /snap/whatsapp-for-linux/31 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-34-1804_77.snap on /snap/gnome-3-34-1804/77 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_2284.snap on /snap/core18/2284 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/code_85.snap on /snap/code/85 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-38-2004_87.snap on /snap/gnome-3-38-2004/87 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1519.snap on /snap/gtk-common-themes/1519 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/snap-store_558.snap on /snap/snap-store/558 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/bare_5.snap on /snap/bare/5 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_161.snap on /snap/gnome-3-28-1804/161 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,nodev,noexec,relatime,size=390848k,mode=755,inode64)
nsfs on /run/snapd/ns/canonical-livepatch.mnt type nsfs (rw)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=390844k,mode=700,uid=1000,gid=1000,inode64)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
nsfs on /run/snapd/ns/snap-store.mnt type nsfs (rw)
/var/lib/snapd/snaps/snapd_14549.snap on /snap/snapd/14549 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_12603.snap on /snap/core/12603 type squashfs (ro,nodev,relatime,x-gdu.hide)
nsfs on /run/snapd/ns/whatsapp-for-linux.mnt type nsfs (rw)
/var/lib/snapd/snaps/core20_1328.snap on /snap/core20/1328 type squashfs (ro,nodev,relatime,x-gdu.hide)
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal
Linux krishn 5.13.0-27-generic #29~20.04.1-Ubuntu SMP Fri Jan 14 00:32:30 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by wildmanne39 on 2022-01-28
Person is no longer here so thread closed, thanks to everyone that participated.

---

