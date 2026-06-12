---
title: "The system keeps trying to mount Microsoft reserved partition"
date: 2017-02-05
forum: General Help
---

### Post by skarux on 2017-02-05
Hi everyone,
I have recently noticed that after logging in I can hear the disk working a lot with no program actually running (except Unity and another couple of standard services);
investigating a little bit I have seen in [FONT=courier new]dmesg[/FONT] that it tries to mount Microsoft reserved partition using the available file systems (ext4, fat, HFS+,qnx4, ufs, etc..) but I really don't understand why (in [FONT=courier new]/etc/fstab[/FONT] there is no reference to it) and I am a bit afraid that it could corrupt in some way that partition and Windows installation.

[FONT=courier new]dmesg[/FONT] output:
```

[  871.637310] xor: automatically using best checksumming function: avx
[  871.767344] Btrfs loaded, crc32c=crc32c-intel
[  872.693135] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  872.694156] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  872.695233] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  872.696260] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda4
[  872.697267] FAT-fs (sda4): bogus number of reserved sectors
[  872.697269] FAT-fs (sda4): Can't find a valid FAT filesystem
[  872.700529] XFS (sda4): Invalid superblock magic number
[  872.704417] FAT-fs (sda4): bogus number of reserved sectors
[  872.704422] FAT-fs (sda4): Can't find a valid FAT filesystem
[  872.707666] VFS: Can't find a Minix filesystem V1 | V2 | V3 on device sda4.
[  872.767259] hfsplus: unable to find HFS+ superblock
[  872.768654] qnx4: no qnx4 filesystem (no root dir).
[  872.769548] ufs: You didn't specify the type of your ufs filesystem
               
               mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
               
               >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[  872.769889] ufs: ufs_fill_super(): bad magic number
[  872.772050] hfs: can't find a HFS filesystem on dev sda4
[  887.027346] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  887.028361] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  887.029310] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  887.030201] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda4
[  887.031095] FAT-fs (sda4): bogus number of reserved sectors
[  887.031097] FAT-fs (sda4): Can't find a valid FAT filesystem
[  887.033972] XFS (sda4): Invalid superblock magic number
[  887.036163] FAT-fs (sda4): bogus number of reserved sectors
[  887.036167] FAT-fs (sda4): Can't find a valid FAT filesystem
[  887.039155] VFS: Can't find a Minix filesystem V1 | V2 | V3 on device sda4.
[  887.040210] hfsplus: unable to find HFS+ superblock
[  887.041160] qnx4: no qnx4 filesystem (no root dir).
[  887.042012] ufs: You didn't specify the type of your ufs filesystem
               
               mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
               
               >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[  887.042201] ufs: ufs_fill_super(): bad magic number
[  887.044190] hfs: can't find a HFS filesystem on dev sda4
[  889.933478] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  889.934454] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  889.935387] EXT4-fs (sda4): VFS: Can't find ext4 filesystem
[  889.936328] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda4
[  889.937314] FAT-fs (sda4): bogus number of reserved sectors
[  889.937317] FAT-fs (sda4): Can't find a valid FAT filesystem
[  889.940577] XFS (sda4): Invalid superblock magic number
[  889.942780] FAT-fs (sda4): bogus number of reserved sectors
[  889.942783] FAT-fs (sda4): Can't find a valid FAT filesystem
[  889.945559] VFS: Can't find a Minix filesystem V1 | V2 | V3 on device sda4.
[  889.946537] hfsplus: unable to find HFS+ superblock
[  889.947449] qnx4: no qnx4 filesystem (no root dir).
[  889.948321] ufs: You didn't specify the type of your ufs filesystem
               
               mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
               
               >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[  889.948517] ufs: ufs_fill_super(): bad magic number
[  889.950419] hfs: can't find a HFS filesystem on dev sda4


```

[FONT=courier new]fdisk[/FONT]
```

lao@o:~$ sudo fdisk -l
Device          Start        End   Sectors   Size Type
/dev/sda1        2048    2050047   2048000  1000M Windows recovery environment
/dev/sda2     2050048    2582527    532480   260M EFI System
/dev/sda3     2582528    4630527   2048000  1000M Lenovo boot partition
/dev/sda4     4630528    4892671    262144   128M Microsoft reserved
/dev/sda5     4892672  590830171 585937500 279,4G Microsoft basic data
/dev/sda6   590831616 1333018623 742187008 353,9G Microsoft basic data
/dev/sda7  1927702528 1953523711  25821184  12,3G Windows recovery environment
/dev/sda8  1333018624 1918955519 585936896 279,4G Linux filesystem
/dev/sda9  1918955520 1927702527   8747008   4,2G Linux swap

Partition table entries are not in disk order.


```

[FONT=courier new]fstab[/FONT]
```

lao@o:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=87d8910a-74e1-4307-bc18-6303146e5c01 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=30AD-8F94  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda9 during installation
UUID=e38b191a-d0ea-4e59-aae4-4838f31bc26e none            swap    sw              0       0

/dev/sda5    /mnt/win    ntfs-3g    auto,umask=000    0    0
/dev/sda6    /mnt/DATA    ntfs-3g   auto,umask=000    0    0

```

The system is an Ubuntu 16.10 installation with the following kernel
Linux o 4.8.0-34-generic #36-Ubuntu SMP Wed Dec 21 17:24:18 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ajgreeny on 2017-02-05
Is there some good reason for using the /dev/sda5 and sda6 naming of partitions instead of the UUIDs?

The former can change, so sda5 may not always be sda5 on every boot, which can cause problems, so to investigate further show us the output of ```
sudo blkid -c /dev/null
``` followed by ```
sudo parted -l
``` and finally ```
mount
```

---

### Post by skarux on 2017-02-05
I have always used partition numbers in fstab simply because it looks more readable to me;
however this is the output that you asked for:

```

lao@o:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="WINRE_DRV" UUID="DA3AAB9A3AAB7265" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="b0a16303-c9e7-421c-9dbf-88e324b2210d"
/dev/sda2: LABEL="SYSTEM_DRV" UUID="30AD-8F94" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="821ec7b2-1bac-4fbb-9c55-882ac1cef7a8"
/dev/sda3: LABEL="LRS_ESP" UUID="3AB4-4437" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="7a06bee1-73cb-4c56-8aa6-4cdc25893d5c"
/dev/sda4: PARTLABEL="Microsoft reserved partition" PARTUUID="9c24c9db-c692-4f34-b051-d129cd720da1"
/dev/sda5: UUID="9ABE70CABE70A105" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="90944915-42f9-4210-a18d-eef1718ef2f4"
/dev/sda6: LABEL="DATA" UUID="CE9EC48F9EC4720F" TYPE="ntfs" PARTUUID="857035eb-eb26-4858-846a-0d78b3ad118a"
/dev/sda7: LABEL="PBR_DRV" UUID="D60CBED00CBEAB3F" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="95a402a6-4508-440c-8e7f-85d6ed4b3697"
/dev/sda8: UUID="87d8910a-74e1-4307-bc18-6303146e5c01" TYPE="ext4" PARTUUID="2a2125ce-3c79-4981-a74d-03e0705f6cc9"
/dev/sda9: UUID="e38b191a-d0ea-4e59-aae4-4838f31bc26e" TYPE="swap" PARTUUID="7be458aa-74b9-4dbc-be44-ae1d1d518738"

```

```

lao@o:~$ sudo parted -l
Model: ATA ST1000LM014-SSHD (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs            Basic data partition          hidden, diag
 2      1050MB  1322MB  273MB   fat32           EFI system partition          boot, hidden, esp
 3      1322MB  2371MB  1049MB  fat32           Basic data partition          hidden
 4      2371MB  2505MB  134MB                   Microsoft reserved partition  msftres
 5      2505MB  303GB   300GB   ntfs            Basic data partition          msftdata
 6      303GB   683GB   380GB   ntfs                                          msftdata
 8      683GB   983GB   300GB   ext4
 9      983GB   987GB   4478MB  linux-swap(v1)
 7      987GB   1000GB  13,2GB  ntfs            Basic data partition          hidden, diag

```

```

lao@o:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4015220k,nr_inodes=1003805,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=807324k,mode=755)
/dev/sda8 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=11784)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda5 on /mnt/win type fuseblk (rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda6 on /mnt/DATA type fuseblk (rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=807320k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

```

---

### Post by ajgreeny on 2017-02-06
In your /etc/fstab  file see if things improve if you replace  **/dev/sda5** with **UUID=9ABE70CABE70A105**
and also replace **/dev/sda6** with **UUID=CE9EC48F9EC4720F**

After the edit run command ```
sudo mount -a
``` and if there is no output and terminal returns ti the prompt, all is well with fstab.

I am just a bit suspicious that at boot the partitions may move from sda5 etc etc to some other numbered partition in your OS particularly as you have such a complicated partition layout and a dual boot with Windows, about which I now know almost nothing.

---

### Post by skarux on 2017-02-07
I have substituted the partition numbers with the UUIDs in fstab but the problem is always there; in the meanwhile I have also updated to 4.8.0-37-generic but the problem is always there.

---

### Post by ajgreeny on 2017-02-07
In that case I have no idea what is going on, I'm afraid, and I do not know enough about Windows to have any idea about the hidden partitions, or what they are for.

---

### Post by skarux on 2017-02-07
The problem is not the purpose of that partition, is why linux is attempting to mount if it is not configured anywhere to do so; 
if for any reason I add a new partition with an unknown file system why should it try to mount it? This thing does not make any sense to me.
Is there any way to put a partition in a sort of "blacklist" like I could do for mods or devices?

---

### Post by The Cog on 2017-02-07
I don't think this is anything to do with fstab. The dmesg output is from 13 minutes after the system booted. And something is trying all different filesystem types to get it mounted - it's trying FAT, EXT*, squashfs, vfs, hfs, hfs+, qnx4, ufs and probably others. There is even what looks to me like an error message from the mount command in there. 

You could try running ```
p=$(pgrep mount) && ps -f $p
``` command occasionally. If it outputs anything, then PPID is the id of the process that called mount.

---

