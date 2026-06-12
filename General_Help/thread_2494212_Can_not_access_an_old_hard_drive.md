---
title: "Can not access an old hard drive"
date: 2024-01-08
forum: General Help
---

### Post by old-dog137 on 2024-01-08
I am using 20.04.06 and just hooked up an old hard drive that has information I want to download.  It says I don't have permission and am not the owner.  I know the password on the old HD.  

I'd appreciate any help.

---

### Post by guiverc on 2024-01-09
> **old-dog137 said:**
> I am using 20.04.06 and just hooked up an old hard drive that has information I want to download.  It says I don't have permission and am not the owner.  I know the password on the old HD.  

I'd appreciate any help.

You mention a release (20.04) but not if this is Ubuntu 20.04 LTS Server? or Ubuntu 20.04 LTS Desktop?

You can explore what is on a system using command (*ideal for server*), eg. using `fdisk -l` I can get a report like

```

Disk /dev/sda: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: TOSHIBA KSG60ZMV
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: CF15687E-D6E0-4FA5-B4A1-3A093258EA5B

Device         Start       End   Sectors  Size Type
/dev/sda1       2048    206847    204800  100M EFI System
/dev/sda2     206848    239615     32768   16M Microsoft reserved
/dev/sda3     239616  92796927  92557312 44.1G EFI System
/dev/sda4  498835456 500115455   1280000  625M Windows recovery environment
/dev/sda5  297035776 298084351   1048576  512M EFI System
/dev/sda6   92796928 297035209 204238282 97.4G Linux filesystem
/dev/sda7  298084352 498835455 200751104 95.7G Linux filesystem

```

for my existing system, though if using a Desktop system I may use a GUI tool like `gparted` which presents the same detail in a different manner.

What I'd look for there is what FILE-SYSTEM, so I know how to `mount` it.  The `gparted` output shows me that, but if using a server I may use

```

guiverc@d7050-next:/de2900/lubuntu_64$   sudo blkid
/dev/sda6: LABEL="ubu_next" UUID="84ffd64e-aa9b-44b5-9d29-7ca799787195" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="2705c9b7-d86a-1d4b-8414-7a43db1b6202"
..

```

where sda6 which showed only as a *Linux filesystem* in my example `fdisk` output shows as EXT4.

Once I know the file-system of the drive, I can attempt to `mount`, which can be done in various different ways too, with options varying on type of file-system (*where you gave no details*) with some easier than other (ext4 being easy, needing no special options)

Most drives do not have passwords; and you didn't indicate what password you're talking about... but I'm aware than really old IBM Thinkpads as example did have an option to ENCRYPT data using the machine *firmware*, which required you to use that password to DECRYPT data, but you needed the same *firmware *in the machine using that drive as well as password in order for it to be decrypted.. Chance are your *password* may only be a 'user password that isn't required to access data (*only login when the old system is being used, but you're using it only as a data drive thus it isn't required here, only your `sudo` password is required*), but I'm unsure.

---

### Post by old-dog137 on 2024-01-09
> **guiverc said:**
> You mention a release (20.04) but not if this is Ubuntu 20.04 LTS Server? or Ubuntu 20.04 LTS Desktop?

You can explore what is on a system using command (*ideal for server*), eg. using `fdisk -l` I can get a report like

```

Disk /dev/sda: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: TOSHIBA KSG60ZMV
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: CF15687E-D6E0-4FA5-B4A1-3A093258EA5B

Device         Start       End   Sectors  Size Type
/dev/sda1       2048    206847    204800  100M EFI System
/dev/sda2     206848    239615     32768   16M Microsoft reserved
/dev/sda3     239616  92796927  92557312 44.1G EFI System
/dev/sda4  498835456 500115455   1280000  625M Windows recovery environment
/dev/sda5  297035776 298084351   1048576  512M EFI System
/dev/sda6   92796928 297035209 204238282 97.4G Linux filesystem
/dev/sda7  298084352 498835455 200751104 95.7G Linux filesystem

```

for my existing system, though if using a Desktop system I may use a GUI tool like `gparted` which presents the same detail in a different manner.

What I'd look for there is what FILE-SYSTEM, so I know how to `mount` it.  The `gparted` output shows me that, but if using a server I may use

```

guiverc@d7050-next:/de2900/lubuntu_64$   sudo blkid
/dev/sda6: LABEL="ubu_next" UUID="84ffd64e-aa9b-44b5-9d29-7ca799787195" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="2705c9b7-d86a-1d4b-8414-7a43db1b6202"
..

```

where sda6 which showed only as a *Linux filesystem* in my example `fdisk` output shows as EXT4.

Once I know the file-system of the drive, I can attempt to `mount`, which can be done in various different ways too, with options varying on type of file-system (*where you gave no details*) with some easier than other (ext4 being easy, needing no special options)

Most drives do not have passwords; and you didn't indicate what password you're talking about... but I'm aware than really old IBM Thinkpads as example did have an option to ENCRYPT data using the machine *firmware*, which required you to use that password to DECRYPT data, but you needed the same *firmware *in the machine using that drive as well as password in order for it to be decrypted.. Chance are your *password* may only be a 'user password that isn't required to access data (*only login when the old system is being used, but you're using it only as a data drive thus it isn't required here, only your `sudo` password is required*), but I'm unsure.

It's 20.04.6 LTS Desktop.

---

### Post by ajgreeny on 2024-01-09
What OS was used on the computer from which this old disk was removed?

If it was Linux of any distro you should be able to se the content and also download it using root, ie, commands starting with sudo which gives you as user temporary root permission.
If it was previously on a Windows machine and is NTFS it may be locked from your Linux OS by being flagged as still in use by Windows,though what you have told us so far does not immediately point in that direction.

---

### Post by ActionParsnip on 2024-01-09
What is the output of
```

sudo fdisk -l
mount

```

---

### Post by old-dog137 on 2024-01-11
> **ActionParsnip said:**
> What is the output of
```

sudo fdisk -l
mount

```
```

skippy@skippy-ThinkStation-P620:~$ sudo fdisk -l
[sudo] password for skippy: 
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 158.91 MiB, 166608896 bytes, 325408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 74.12 MiB, 77713408 bytes, 151784 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 55.68 MiB, 58363904 bytes, 113992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 194.38 MiB, 203808768 bytes, 398064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 216.71 MiB, 227217408 bytes, 443784 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 45.95 MiB, 48156672 bytes, 94056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 105.78 MiB, 110895104 bytes, 216592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 953.89 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: SAMSUNG MZVL21T0HCLR-00BL7              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 185A7C1A-AC1E-4F72-83D2-41FD5E70BC3E

Device            Start        End    Sectors  Size Type
/dev/nvme0n1p1     2048    1802240    1800193  879M EFI System
/dev/nvme0n1p2  1804288   12290047   10485760    5G EFI System
/dev/nvme0n1p3 12290048 2000409230 1988119183  948G Linux filesystem


Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WD5000AAKX-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000899a3

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1             63  15631244  15631182   7.5G 82 Linux swap / Solaris
/dev/sda2  *    15632384 976771071 961138688 458.3G 83 Linux




Disk /dev/loop15: 496.9 MiB, 521015296 bytes, 1017608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 349.71 MiB, 366678016 bytes, 716168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 208.4 MiB, 218509312 bytes, 426776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 63.48 MiB, 66547712 bytes, 129976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 375.32 MiB, 393539584 bytes, 768632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 126.55 MiB, 132685824 bytes, 259152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 146.7 MiB, 153161728 bytes, 299144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 139.76 MiB, 146534400 bytes, 286200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 450.16 MiB, 472018944 bytes, 921912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 321.8 MiB, 336678912 bytes, 657576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 66.58 MiB, 69795840 bytes, 136320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 320.45 MiB, 336003072 bytes, 656256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 145.98 MiB, 153042944 bytes, 298912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 164.84 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 91.7 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 126.55 MiB, 132685824 bytes, 259152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 164.78 MiB, 172761088 bytes, 337424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 55.68 MiB, 58363904 bytes, 113992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 105.84 MiB, 110960640 bytes, 216720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop36: 116.49 MiB, 122138624 bytes, 238552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 376.85 MiB, 395137024 bytes, 771752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 496.10 MiB, 521121792 bytes, 1017816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 66.55 MiB, 69771264 bytes, 136272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 63.93 MiB, 67014656 bytes, 130888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 349.71 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 73.92 MiB, 77492224 bytes, 151352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 12.33 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 448.94 MiB, 470728704 bytes, 919392 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 158.92 MiB, 166621184 bytes, 325432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

```

skippy@skippy-ThinkStation-P620:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=16226736k,nr_inodes=4056684,mode=755,inode64)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=3267776k,mode=755,inode64)
/dev/nvme0n1p3 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k,inode64)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755,inode64)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
bpf on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/misc type cgroup (rw,nosuid,nodev,noexec,relatime,misc)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=38796)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/bare_5.snap on /snap/bare/5 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/chromium_2719.snap on /snap/chromium/2719 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core22_1033.snap on /snap/core22/1033 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core18_2796.snap on /snap/core18/2796 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/smplayer_76.snap on /snap/smplayer/76 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/urh_9.snap on /snap/urh/9 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/snap-store_599.snap on /snap/snap-store/599 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core_16091.snap on /snap/core/16091 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/chromium_2724.snap on /snap/chromium/2724 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/digikam_78.snap on /snap/digikam/78 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-38-2004_143.snap on /snap/gnome-3-38-2004/143 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-42-2204_141.snap on /snap/gnome-42-2204/141 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-38-2004_140.snap on /snap/gnome-3-38-2004/140 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/kf5-5-108-qt-5-15-10-core22_5.snap on /snap/kf5-5-108-qt-5-15-10-core22/5 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/jdownloader2_17.snap on /snap/jdownloader2/17 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/jdownloader2_20.snap on /snap/jdownloader2/20 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_161.snap on /snap/gnome-3-28-1804/161 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/smplayer_86.snap on /snap/smplayer/86 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/vlc_3721.snap on /snap/vlc/3721 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core18_2812.snap on /snap/core18/2812 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core20_2015.snap on /snap/core20/2015 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/vlc_3078.snap on /snap/vlc/3078 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/cups_1024.snap on /snap/cups/1024 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_198.snap on /snap/gnome-3-28-1804/198 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/kf5-5-105-qt-5-15-9-core22_11.snap on /snap/kf5-5-105-qt-5-15-9-core22/11 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/ytdownloader_72.snap on /snap/ytdownloader/72 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core_16202.snap on /snap/core/16202 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/ytdownloader_74.snap on /snap/ytdownloader/74 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/digikam_74.snap on /snap/digikam/74 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core20_2105.snap on /snap/core20/2105 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core22_864.snap on /snap/core22/864 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/cups_980.snap on /snap/cups/980 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/snap-store_959.snap on /snap/snap-store/959 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-42-2204_132.snap on /snap/gnome-42-2204/132 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/shotcut_1298.snap on /snap/shotcut/1298 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1535.snap on /snap/gtk-common-themes/1535 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/shotcut_1312.snap on /snap/shotcut/1312 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,nodev,noexec,relatime,size=3267776k,mode=755,inode64)
tmpfs on /run/user/1001 type tmpfs (rw,nosuid,nodev,relatime,size=3267776k,mode=700,uid=1001,gid=1001,inode64)
gvfsd-fuse on /run/user/1001/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1001,group_id=1001)
nsfs on /run/snapd/ns/cups.mnt type nsfs (rw)
/dev/fuse on /run/user/1001/doc type fuse (rw,nosuid,nodev,relatime,user_id=1001,group_id=1001)
nsfs on /run/snapd/ns/snap-store.mnt type nsfs (rw)
skippy@skippy-ThinkStation-P620:~$

```

---

### Post by old-dog137 on 2024-01-14
So this is hopeless?

---

### Post by oldfred on 2024-01-14
Please use Code Tags with terminal output.
Easy to add with Forum's advanced Editor & # icon

Also loop mounts from snaps & snaps in mount do not add anything, just do not post them.

It might help if you told us what drive/partition in what you posted is the issue? Is it sda & sda2?

---

### Post by old-dog137 on 2024-01-15
> **oldfred said:**
> Please use Code Tags with terminal output.
Easy to add with Forum's advanced Editor & # icon

Also loop mounts from snaps & snaps in mount do not add anything, just do not post them.

It might help if you told us what drive/partition in what you posted is the issue? Is it sda & sda2?

The problem drive, on which I can view but not copy files, is /dev//sda1

The bootable drive on my machine is /dev/nvme0n1p1

Sorry about my posting format.  I'm not familiar with "code tags" or "loop mounts".

---

### Post by yancek on 2024-01-15
> The problem drive, on which I can view but not copy files, is /dev//sda1 

In post #3, sda1 shows as an EFI partition.  In post #6, sda1 shows as a swap partition.  Which is it?  Did you change the partition?  Did you add another drive/usb and change the device?
When you are posting in the input text box, you will see icons above the input box.  Mouse over them to see what each is.
The loop mount sections from the fdisk output are not needed so remove them before you post.

---

### Post by old-dog137 on 2024-01-15
> **yancek said:**
> In post #3, sda1 shows as an EFI partition.  In post #6, sda1 shows as a swap partition.  Which is it?  Did you change the partition?  Did you add another drive/usb and change the device?
When you are posting in the input text box, you will see icons above the input box.  Mouse over them to see what each is.
The loop mount sections from the fdisk output are not needed so remove them before you post.

I did not touch any partitions. I did not add or remove any devices.  I have no explanation.

---

### Post by tea for one on 2024-01-16
Looks like a misunderstanding is in play here.
Post no. 3 is an example of fdisk output originally supplied by [COLOR="#0000FF"]guiverc[/COLOR] in post no. 2
Post no. 6 is the fdisk output from [COLOR="#0000FF"]old-dog137[/COLOR]

However, it appears that the OP wishes to access sda2 rather than the swap partition sda1.

---

### Post by old-dog137 on 2024-01-18
> **tea for one said:**
> However, it appears that the OP wishes to access sda2 rather than the swap partition sda1.

Yes.

---

### Post by dragonfly41 on 2024-01-19
But ... /dev/sda2 is not Linux ...

[COLOR=#000000][FONT=&quot]/dev/sda2     206848    239615     32768   16M Microsoft reserved ... 

Surely from post#2 you are looking at /dev/sda6 and /dev/sda7

Perhaps as last resort if other methods fail try testdisk (running in LiveUSB) to inspect your drive .. BUT .. you need a container/partition large enough into which you save recovered files.  You cannot recover into the target drive or you overwrite the data to be recovered. Be warned. It must be have target space such as another partition or drive with space at least as large as the data to be recovered. Testdisk is a last resort if other approaches fail. On the other hand it is a diagnostic tool useful to learn. From LiveUSB  .. sudo apt-install testdisk[/FONT][/COLOR]

---

### Post by deadflowr on 2024-01-19
> **dragonfly41 said:**
> But ... /dev/sda2 is not Linux ...

[COLOR=#000000][FONT=&quot]/dev/sda2     206848    239615     32768   16M Microsoft reserved ... 

Surely from post#2 you are looking at /dev/sda6 and /dev/sda7

Perhaps as last resort if other methods fail try testdisk (running in LiveUSB) to inspect your drive .. BUT .. you need a container/partition large enough into which you save recovered files.  You cannot recover into the target drive or you overwrite the data to be recovered. Be warned. It must be have target space such as another partition or drive with space at least as large as the data to be recovered. Testdisk is a last resort if other approaches fail. On the other hand it is a diagnostic tool useful to learn. From LiveUSB  .. sudo apt-install testdisk[/FONT][/COLOR]

Post #12 explains it.
The OP only posted the fdisk results in post #6, which shows two drives, one an nvme drive and the other an old western digital drive marked as /dev/sda, which only has 2 partitions, with sda1 as a swap partition. sda2 is some linux partitioned drive, that's all we know about the drive. It's hard to see that because fdisk outputs all that loop device output as well.

I'd want to know if the partition mounts or not before going further.
And how they are attempting to mount it.
There is no indication that the drive does not mount, but rather they are being denied access because of a lack of ownership.
They mention a password, but it's unclear if it is a password for the drive itself or a password for the system that used the drive.

---

