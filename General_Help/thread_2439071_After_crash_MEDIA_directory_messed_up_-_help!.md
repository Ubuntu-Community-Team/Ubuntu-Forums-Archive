---
title: "After crash MEDIA directory messed up - help!"
date: 2020-03-22
forum: General Help
---

### Post by Brent_Santin on 2020-03-22
During testing of some recording software I had several hard crashes that locked up my machine, and to get out of this each time I had to do a hard shut down (essentially cutting power).

Now, in my /media directory, I am seeing some erroneous information of "ghost" drives that aren't there and others that are duplicated. These are drives that were mounted during crash and are now "ghosts" that I cannot unmount.

```
**brent@brent-OptiPlex-GX620:/media/brent$** ls
Amiga_Archive_01  Media_Drive  Media_Drive1  Media_Drive2
```

**Amiga_Archive_01** is a CD-ROM disk that is not longer inserted in the drive. Even though it shouldn't exist, I can enter the directory but there's nothing there.
**Media_Drive** should go to an internal hard drive where I store all my media files, but now when I try to access it I get the error: **bash: cd: Media_Drive: Permission denied**
**Media_Drive1** showed up new after one of the hard resets, I never created this. It gives the same error as above when I try to cd into it.
**Media_Drive2** also showed up after one of the resets, and I can access it, where it shows what should be in Media_Drive (the original name of the hard drive).

I did try deleting Amiga_Archive_01 but got "Permission Denied".
They survive reboots.

I also tried the following which did not work:

```
brent@brent-OptiPlex-GX620:/media/brent$ sudo umount /media/Amiga_Archive_01
[sudo] password for brent: 
umount: /media/Amiga_Archive_01: no mount point specified.

```


The output of "mount" command shows the following (I don't know what any of this means or if it is helpful):

```
brent@brent-OptiPlex-GX620:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1509272k,nr_inodes=377318,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=306328k,mode=755)
/dev/sdb5 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=42,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12589)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/var/lib/snapd/snaps/kde-frameworks-5-core18_32.snap on /snap/kde-frameworks-5-core18/32 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/kde-frameworks-5-qt-5-14-core18_3.snap on /snap/kde-frameworks-5-qt-5-14-core18/3 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/fsuae_73.snap on /snap/fsuae/73 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_116.snap on /snap/gnome-3-28-1804/116 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/skype_118.snap on /snap/skype/118 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_8689.snap on /snap/core/8689 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1440.snap on /snap/gtk-common-themes/1440 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1668.snap on /snap/core18/1668 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/fsuae_61.snap on /snap/fsuae/61 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/kdenlive_23.snap on /snap/kdenlive/23 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/kdenlive_22.snap on /snap/kdenlive/22 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/skype_115.snap on /snap/skype/115 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/snapd_6434.snap on /snap/snapd/6434 type squashfs (ro,nodev,relatime,x-gdu.hide)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=306324k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,noexec,relatime,size=306328k,mode=755)
nsfs on /run/snapd/ns/kdenlive.mnt type nsfs (rw)

```
Can anyone please help me fix this? Kind of worrisome!

Thanks.

[[IMG]https://i.postimg.cc/rR4hWPNg/Screenshot-from-2020-03-22-12-33-19.png[/IMG]]("https://postimg.cc/rR4hWPNg")

---

### Post by Brent_Santin on 2020-03-22
Solution found:
[B]
sudo rm -r /media/brent/<name of ghost drive to be remove>[/B]

---

### Post by Impavidus on 2020-03-23
When you used the gui tools to mount something (or let it happen automatically by inserting a usb drive), the tool first created a mount point, being an empty directory in /media/your_user_name, then mounted the filesystem at that empty directory. When you use the same tool to unmount that filesystem (or simply shut down your computer), the filesystems are unmounted and the mountpoints deleted.  By forcing a hard shutdown of your computer, those tools got no opportunity to delete the mountpoints, so they were left in place. You did the right thing to remove them.

---

