---
title: "mess in mount point after upgrade from 20.04 to 22.04"
date: 2023-02-21
forum: General Help
---

### Post by luca-dgh on 2023-02-21
I made an upgrade from Ubuntu 20.04 to Ubuntu 22.04, everything was fine, the system works well, excellent. But today, after a week, I realized something weird.
I have a nvme drive (1 TB) and a ssd drive, the nvme is the main, the ssd hosts only a virtual machine.
The nvme drive has 10 partitions, in the #2 there is the system, in the #3 there is a clone of the system for experiments purposes, #4 is the home and the others partitions are for my data.
Today I opened gparted and I saw that the partition #2 (sys1) is mounted on ```
/dev/nvme0n1p2 on /var/snap/firefox/common/host-hunspell type ext4 (ro,noexec,noatime,errors=remount-ro) [sys1]
``` instead to be mounted on ```
/
``` How is it possible? My system is working, but no file syhstem is mounted on "/".
What is that mess? How to fix it?

```
luca@pc-sala:~$ sudo mount -l
[sudo] contraseña para root: 
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2951664k,nr_inodes=737916,mode=755,inode64)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=601688k,mode=755,inode64)
/dev/nvme0n1p2 on / type ext4 (rw,relatime,errors=remount-ro) [sys1]
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k,inode64)
cgroup2 on /sys/fs/cgroup type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate,memory_recursiveprot)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
bpf on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=25623)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
none on /run/credentials/systemd-sysusers.service type ramfs (ro,nosuid,nodev,noexec,relatime,mode=700)
/var/lib/snapd/snaps/bare_5.snap on /snap/bare/5 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core18_2697.snap on /snap/core18/2697 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core18_2667.snap on /snap/core18/2667 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core20_1695.snap on /snap/core20/1695 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core22_509.snap on /snap/core22/509 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core20_1822.snap on /snap/core20/1822 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/core22_522.snap on /snap/core22/522 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/cups_872.snap on /snap/cups/872 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/cups_836.snap on /snap/cups/836 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_145.snap on /snap/gnome-3-28-1804/145 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/firefox_2356.snap on /snap/firefox/2356 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_161.snap on /snap/gnome-3-28-1804/161 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-38-2004_115.snap on /snap/gnome-3-38-2004/115 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-38-2004_119.snap on /snap/gnome-3-38-2004/119 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gnome-42-2204_56.snap on /snap/gnome-42-2204/56 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1534.snap on /snap/gtk-common-themes/1534 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/onlyoffice-desktopeditors_133.snap on /snap/onlyoffice-desktopeditors/133 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/onlyoffice-desktopeditors_144.snap on /snap/onlyoffice-desktopeditors/144 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1535.snap on /snap/gtk-common-themes/1535 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/software-boutique_54.snap on /snap/software-boutique/54 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/snapd_18357.snap on /snap/snapd/18357 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/telegram-desktop_4593.snap on /snap/telegram-desktop/4593 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/software-boutique_57.snap on /snap/software-boutique/57 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/telegram-desktop_4627.snap on /snap/telegram-desktop/4627 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/ubuntu-mate-welcome_709.snap on /snap/ubuntu-mate-welcome/709 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/var/lib/snapd/snaps/ubuntu-mate-welcome_714.snap on /snap/ubuntu-mate-welcome/714 type squashfs (ro,nodev,relatime,errors=continue,x-gdu.hide)
/dev/nvme0n1p2 on /var/snap/firefox/common/host-hunspell type ext4 (ro,noexec,noatime,errors=remount-ro) [sys1]
/dev/nvme0n1p4 on /home type ext4 (rw,relatime) [home]
/dev/nvme0n1p5 on /media/didattica type ext4 (rw,relatime) [didattica]
/dev/nvme0n1p8 on /media/films type ext4 (rw,relatime) [films]
/dev/nvme0n1p7 on /media/musica type ext4 (rw,relatime) [musica]
/dev/sda1 on /media/nvbox type ext4 (rw,relatime) [nvbox]
/dev/nvme0n1p9 on /media/vuota type ext4 (rw,relatime) [vuota]
/dev/nvme0n1p6 on /media/dati type ext4 (rw,relatime) [dati]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,nodev,noexec,relatime,size=601688k,mode=755,inode64)
nsfs on /run/snapd/ns/cups.mnt type nsfs (rw)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=601684k,nr_inodes=150421,mode=700,uid=1000,gid=1000,inode64)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
portal on /run/user/1000/doc type fuse.portal (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
nsfs on /run/snapd/ns/firefox.mnt type nsfs (rw)
luca@pc-sala:~$ 

```

```
luca@pc-sala:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# /
UUID=70fca47c-4e5f-40a4-8e30-9d2040d74bf4 /               ext4    errors=remount-ro 0       1

# /sys2
UUID=059fd4db-327e-4a6f-9cd3-46a96bd18259 /sys2           ext4    defaults        0       2

# /boot/efi
#UUID=0fe26777-441e-4028-8b56-bb44c4271bfe  /boot/efi      vfat    umask=0077      0       1

# /home
UUID=12bb101c-c714-4d65-8dce-8c2a5f83c577 /home           ext4    defaults        0       2

# /media/dati
UUID=ee711e3f-bf8f-4a61-8a8b-003c01dca56b /media/dati     ext4    defaults        0       2

# /media/didattica
UUID=64015756-2d52-40ec-bb58-89018be4708d /media/didattica ext4    defaults        0       2

# /media/films
UUID=aae7b79e-5b2b-413a-9a53-379cbf50a5b8 /media/films    ext4    defaults        0       2

# /media/musica
UUID=fb0e2751-9b2e-4528-bea5-9090c44fa09a /media/musica   ext4    defaults        0       2

# /media/nvbox
UUID=1ed57a51-9273-49a8-932a-50cfb45512c0 /media/nvbox    ext4    defaults        0       2

# /media/vuota
UUID=83525b9d-8c48-4b81-a7f3-b247f04c3d8f /media/vuota    ext4    defaults        0       2

# swap
UUID=7c509211-9d80-44de-8c35-7f9369ea3782 none            swap    sw              0       0
luca@pc-sala:~$ 

```


```
luca@pc-sala:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 15 feb 21 17:14 059fd4db-327e-4a6f-9cd3-46a96bd18259 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 feb 21 17:14 12bb101c-c714-4d65-8dce-8c2a5f83c577 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 10 feb 21 17:14 1ed57a51-9273-49a8-932a-50cfb45512c0 -> ../../sda1
lrwxrwxrwx 1 root root 15 feb 21 17:14 64015756-2d52-40ec-bb58-89018be4708d -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 feb 21 17:14 70fca47c-4e5f-40a4-8e30-9d2040d74bf4 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 16 feb 21 17:14 7c509211-9d80-44de-8c35-7f9369ea3782 -> ../../nvme0n1p10
lrwxrwxrwx 1 root root 15 feb 21 17:14 83525b9d-8c48-4b81-a7f3-b247f04c3d8f -> ../../nvme0n1p9
lrwxrwxrwx 1 root root 15 feb 21 17:14 aae7b79e-5b2b-413a-9a53-379cbf50a5b8 -> ../../nvme0n1p8
lrwxrwxrwx 1 root root 15 feb 21 17:14 ee711e3f-bf8f-4a61-8a8b-003c01dca56b -> ../../nvme0n1p6
lrwxrwxrwx 1 root root 15 feb 21 17:14 fb0e2751-9b2e-4528-bea5-9090c44fa09a -> ../../nvme0n1p7
luca@pc-sala:~$

```

---

### Post by TheFu on 2023-02-21
To see what's mounted, I prefer this command: 
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

To see all the real storage in a system, I prefer this command:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
If you setup those aliases, you'll never need to type the long, multi-option, versions of the commands again.

I suspect you are confusing fake mounts as abused by the snap subsystem with real storage.

The output from the mount command above is full of useless junk that isn't related to any actual storage use/mount.
```

/dev/nvme0n1p2 on / type ext4 (rw,relatime,errors=remount-ro) [sys1]
/dev/nvme0n1p4 on /home type ext4 (rw,relatime) [home]
/dev/nvme0n1p5 on /media/didattica type ext4 (rw,relatime) [didattica]
/dev/nvme0n1p8 on /media/films type ext4 (rw,relatime) [films]
/dev/nvme0n1p7 on /media/musica type ext4 (rw,relatime) [musica]
/dev/sda1 on /media/nvbox type ext4 (rw,relatime) [nvbox]
/dev/nvme0n1p9 on /media/vuota type ext4 (rw,relatime) [vuota]
/dev/nvme0n1p6 on /media/dati type ext4 (rw,relatime) [dati]

```
Are the only parts that matter and they are in a hard-to-read format.  The suggested aliases correct the ugly format and provide other useful information.

---

### Post by deadflowr on 2023-02-21
That's actually normal and fine.
Your file system is indeed mounted correctly
```
/dev/nvme0n1p2 on / type ext4 (rw,relatime,errors=remount-ro) [sys1]
```
The odd output you show
```
/dev/nvme0n1p2 on /var/snap/firefox/common/host-hunspell type ext4 (ro,noexec,noatime,errors=remount-ro) [sys1]
```
is the known workaround to give firefox access to the hunspell dictionary on the system.

More discussion on it here: [https://forum.snapcraft.io/t/sdb5-mounted-on-firefox/31897/8]("https://forum.snapcraft.io/t/sdb5-mounted-on-firefox/31897/8")

---

### Post by luca-dgh on 2023-02-23
OK, I understand, thx a lot for your answers.
I got surprised to see that unexpected mount point form snap.
Thx a lot again.

---

