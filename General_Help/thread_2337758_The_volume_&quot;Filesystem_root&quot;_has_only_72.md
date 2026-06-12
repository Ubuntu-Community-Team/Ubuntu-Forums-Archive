---
title: "The volume &quot;Filesystem root&quot; has only 721.6 MB disk space remaining"
date: 2016-09-21
forum: General Help
---

### Post by gnvrvikram on 2016-09-21
I am getting the similar message, with the amount of remaining space varying with instance of occurrence,  very regularly. I have followed some of the posts that are similar to problem I have been facing and found out that the problem is specific to that particular case. Most of them who are trying to help have asked to post the outputs of these commands: **df -Th, ****df -h, ****df -i, ****mount, ****sudo parted -l **. So i am attaching the outputs so that the issue can be solved faster.

My system has 12 GB RAM, 32 GB SSD(OS installed on it), 500 GB HDD(for data other than programs and their data). I am using UBUNTU 16.04. Please let me know of any additional requirement for solving my issue. 
```

**df -Th **
 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  5.8G     0  5.8G   0% /dev
tmpfs          tmpfs     1.2G  9.5M  1.2G   1% /run
/dev/sdb3      ext4       26G   24G  756M  97% /
tmpfs          tmpfs     5.9G   85M  5.8G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/loop0     squashfs  222M  222M     0 100% /snap/freecad/4
/dev/loop1     squashfs   75M   75M     0 100% /snap/ubuntu-core/352
/dev/loop2     squashfs   73M   73M     0 100% /snap/ubuntu-core/216
/dev/loop3     squashfs   75M   75M     0 100% /snap/ubuntu-core/423
/dev/sdb1      vfat      511M  3.6M  508M   1% /boot/efi
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     1.2G   80K  1.2G   1% /run/user/1000
/dev/sda3      ext4      138G   71G   61G  54% /media/viksan/Research
 
**df -h**
Filesystem      Size  Used Avail Use% Mounted on
udev            5.8G     0  5.8G   0% /dev
tmpfs           1.2G   17M  1.2G   2% /run
/dev/sdb3        26G   24G  703M  98% /
tmpfs           5.9G  118M  5.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/loop0      222M  222M     0 100% /snap/freecad/4
/dev/loop1       75M   75M     0 100% /snap/ubuntu-core/352
/dev/loop2       73M   73M     0 100% /snap/ubuntu-core/216
/dev/loop3       75M   75M     0 100% /snap/ubuntu-core/423
/dev/sdb1       511M  3.6M  508M   1% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.2G   96K  1.2G   1% /run/user/1000
/dev/sda3       138G   71G   61G  54% /media/viksan/Research
/dev/sda2       230G  214G  3.8G  99% /media/viksan/Entertain
 
**df -i**
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            1519850    621  1519229    1% /dev
tmpfs           1524702    879  1523823    1% /run
/dev/sdb3       1736704 509605  1227099   30% /
tmpfs           1524702    244  1524458    1% /dev/shm
tmpfs           1524702      5  1524697    1% /run/lock
tmpfs           1524702     18  1524684    1% /sys/fs/cgroup
/dev/loop0         6014   6014        0  100% /snap/freecad/4
/dev/loop1        10991  10991        0  100% /snap/ubuntu-core/352
/dev/loop2        10979  10979        0  100% /snap/ubuntu-core/216
/dev/loop3        11285  11285        0  100% /snap/ubuntu-core/423
/dev/sdb1             0      0        0     - /boot/efi
cgmfs           1524702     14  1524688    1% /run/cgmanager/fs
tmpfs           1524702     39  1524663    1% /run/user/1000
/dev/sda3       9158656  45209  9113447    1% /media/viksan/Research
/dev/sda2      15269888  33408 15236480    1% /media/viksan/Entertain
 
**mount**
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=6079400k,nr_inodes=1519850,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1219764k,mode=755)
/dev/sdb3 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/freecad_4.snap on /snap/freecad/4 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-core_352.snap on /snap/ubuntu-core/352 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-core_216.snap on /snap/ubuntu-core/216 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-core_423.snap on /snap/ubuntu-core/423 type squashfs (ro,relatime)
/dev/sdb1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1219764k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda3 on /media/viksan/Research type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
 
**sudo parted -l**
Model: ATA ST500LM021-1KJ15 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 
 
Number  Start   End    Size   File system  Name  Flags
 1      1049kB  100GB  100GB  ext4
 3      100GB   250GB  150GB  ext4
 2      250GB   500GB  250GB  ext4
 
 
Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 
 
Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 3      538MB   28.9GB  28.3GB  ext4
 2      28.9GB  32.0GB  3146MB  linux-swap(v1)
 
**df -Th **
 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  5.8G     0  5.8G   0% /dev
tmpfs          tmpfs     1.2G  9.5M  1.2G   1% /run
/dev/sdb3      ext4       26G   24G  756M  97% /
tmpfs          tmpfs     5.9G   85M  5.8G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/loop0     squashfs  222M  222M     0 100% /snap/freecad/4
/dev/loop1     squashfs   75M   75M     0 100% /snap/ubuntu-core/352
/dev/loop2     squashfs   73M   73M     0 100% /snap/ubuntu-core/216
/dev/loop3     squashfs   75M   75M     0 100% /snap/ubuntu-core/423
/dev/sdb1      vfat      511M  3.6M  508M   1% /boot/efi
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     1.2G   80K  1.2G   1% /run/user/1000
/dev/sda3      ext4      138G   71G   61G  54% /media/viksan/Research
 
**df -h**
Filesystem      Size  Used Avail Use% Mounted on
udev            5.8G     0  5.8G   0% /dev
tmpfs           1.2G   17M  1.2G   2% /run
/dev/sdb3        26G   24G  703M  98% /
tmpfs           5.9G  118M  5.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/loop0      222M  222M     0 100% /snap/freecad/4
/dev/loop1       75M   75M     0 100% /snap/ubuntu-core/352
/dev/loop2       73M   73M     0 100% /snap/ubuntu-core/216
/dev/loop3       75M   75M     0 100% /snap/ubuntu-core/423
/dev/sdb1       511M  3.6M  508M   1% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.2G   96K  1.2G   1% /run/user/1000
/dev/sda3       138G   71G   61G  54% /media/viksan/Research
/dev/sda2       230G  214G  3.8G  99% /media/viksan/Entertain
 
**df -i**
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            1519850    621  1519229    1% /dev
tmpfs           1524702    879  1523823    1% /run
/dev/sdb3       1736704 509605  1227099   30% /
tmpfs           1524702    244  1524458    1% /dev/shm
tmpfs           1524702      5  1524697    1% /run/lock
tmpfs           1524702     18  1524684    1% /sys/fs/cgroup
/dev/loop0         6014   6014        0  100% /snap/freecad/4
/dev/loop1        10991  10991        0  100% /snap/ubuntu-core/352
/dev/loop2        10979  10979        0  100% /snap/ubuntu-core/216
/dev/loop3        11285  11285        0  100% /snap/ubuntu-core/423
/dev/sdb1             0      0        0     - /boot/efi
cgmfs           1524702     14  1524688    1% /run/cgmanager/fs
tmpfs           1524702     39  1524663    1% /run/user/1000
/dev/sda3       9158656  45209  9113447    1% /media/viksan/Research
/dev/sda2      15269888  33408 15236480    1% /media/viksan/Entertain
 
**mount**
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=6079400k,nr_inodes=1519850,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1219764k,mode=755)
/dev/sdb3 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/freecad_4.snap on /snap/freecad/4 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-core_352.snap on /snap/ubuntu-core/352 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-core_216.snap on /snap/ubuntu-core/216 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-core_423.snap on /snap/ubuntu-core/423 type squashfs (ro,relatime)
/dev/sdb1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1219764k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda3 on /media/viksan/Research type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
 
**sudo parted -l**
Model: ATA ST500LM021-1KJ15 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 
 
Number  Start   End    Size   File system  Name  Flags
 1      1049kB  100GB  100GB  ext4
 3      100GB   250GB  150GB  ext4
 2      250GB   500GB  250GB  ext4
 
 
Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 
 
Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 3      538MB   28.9GB  28.3GB  ext4
 2      28.9GB  32.0GB  3146MB  linux-swap(v1)
 

```

---

### Post by &amp;KyT$0P# on 2016-09-21
Troubleshooting this should be pretty much along the same lines as in [this other thread]("https://ubuntuforums.org/showthread.php?t=2331523").

So, first things first, can you please post the output of this command? -
```
cd / ; sudo du -sx $(ls -A) | sort -n
```

---

### Post by oldos2er on 2016-09-21
Thread moved to General Help.

---

