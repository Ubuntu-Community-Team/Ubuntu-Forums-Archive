---
title: "Unable to access another computer's hard drive via usb"
date: 2020-09-05
forum: General Help
---

### Post by ancares on 2020-09-05
Hi all. I recently broke a pc with Ubuntu installed. I took out the hard drive and mounted it on a base connected via USB to another Ubuntu laptop. The problem is that I can't figure out how to browse this drive to get my files back. In the "Disks" application the device appears recognized, but I am not able to get to it via nautilus. Anyone who can help me? Thank you

---

### Post by ActionParsnip on 2020-09-05
What is the output of:
```

sudo parted -l; mount; uname -a; lsb_release -a

```
Thanks

---

### Post by ancares on 2020-09-05
Hi, it outputs: > Modelo: ATA ASN8 240GB (scsi)
Disco /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Táboa de particións: gpt
Disk Flags: 

Número  Inicio  Fin    Tamaño  Sistema de ficheiros  Nome                  Modificadores
 1      1049kB  538MB  537MB   fat32                 EFI System Partition  arranque, esp
 2      538MB   240GB  240GB   ext4


Modelo: WDC WD10 JPCX-24UE4T0 (scsi)
Disco /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Táboa de particións: msdos
Disk Flags: 

Número  Inicio  Fin     Tamaño  Tipo     Sistema de ficheiros  Modificadores
 1      1049kB  1000GB  1000GB  primary                        arranque, lvm


sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=8128036k,nr_inodes=2032009,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=1631240k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=20225)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/core_9804.snap on /snap/core/9804 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_128.snap on /snap/gnome-3-28-1804/128 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1880.snap on /snap/core18/1880 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1885.snap on /snap/core18/1885 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/snapd_8790.snap on /snap/snapd/8790 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1506.snap on /snap/gtk-common-themes/1506 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/blender_45.snap on /snap/blender/45 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-34-1804_36.snap on /snap/gnome-3-34-1804/36 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/vlc_1700.snap on /snap/vlc/1700 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/standard-notes_11.snap on /snap/standard-notes/11 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/snapd_8542.snap on /snap/snapd/8542 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/snap-store_467.snap on /snap/snap-store/467 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/125 type tmpfs (rw,nosuid,nodev,relatime,size=1631236k,mode=700,uid=125,gid=130)
gvfsd-fuse on /run/user/125/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=125,group_id=130)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1631236k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,nodev,noexec,relatime,size=1631240k,mode=755)
nsfs on /run/snapd/ns/snap-store.mnt type nsfs (rw)
/var/lib/snapd/snaps/gimp_292.snap on /snap/gimp/292 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/kde-frameworks-5-core18_32.snap on /snap/kde-frameworks-5-core18/32 type squashfs (ro,nodev,relatime,x-gdu.hide)
nsfs on /run/snapd/ns/gimp.mnt type nsfs (rw)
gvfsd-fuse on /root/.cache/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=0,group_id=0)
/dev/fuse on /root/.cache/doc type fuse (rw,nosuid,nodev,relatime,user_id=0,group_id=0)
Linux gabino-HP-Pavilion-Laptop-14-bf1xx 5.4.0-45-generic #49-Ubuntu SMP Wed Aug 26 13:38:52 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal



Thank you

---

### Post by SeijiSensei on 2020-09-05
Usually if you plug in a USB drive, Ubuntu "mounts" it at /media/username/[some identifier]/.  For instance, I just plugged in an empty USB stick from ADATA. My computer popped up a notification asking if I want to open it with the File Manager. When I said yes, it appears as "/media/seiji/ADATA UFD".  If I decline to mount the device when prompted it doesn't show up at all.

Run the command "df" and see if you have a device called /home/yourusername/something.  If not, you can mount it manually. For temporary mounts, *nix systems provide a /mnt directory.  First you need to see how Linux has named the device.  Use the command "sudo fdisk -l" to see a list of available devices.  You'll probably see a "/dev/sdb1" in the list.  If so, you can mount it with "sudo mount /dev/sdb1 /mnt".  Then you can read to and write from the /mnt directory.

---

### Post by ancares on 2020-09-06
Thank you both for your help. When I tried "sudo mount / dev / sdb1 / mnt", then it printed something like "mount unknown filesystem type 'lvm2_member'", so I figured out the matter.

I went:
> sudo apt-get install lvm2

and now i can access the drive without problem!

---

