---
title: "can't edit files on second HDD"
date: 2017-10-03
forum: General Help
---

### Post by Hasimir on 2017-10-03
Suddenly today I find myself unable to edit (cut, delete, rename, etc) files and folders on my secondary HDD.
The files properties look fine, I have read-write-execute access, I can open and run the files, but nothing more.

Any ideas about what happened and how to fix it?
Or how to try and diagnose the problem?

Thanks :)

EDIT:
running Ubuntu Genome 17.04 with kernel 4.13.4

---

### Post by Impavidus on 2017-10-03
To move/delete/rename files and directories, you need write permission on the directory containing them, known as the parent directory. You don't need permissions on the file you want to delete. But I don't think that's your problem.

Whenever there's an error accessing a file system, it may be remounted read-only to prevent further damage. Run **mount**, find the line for your secondary hard drive and see if there's the ro (for read only) option. The file system may require a check. This may happen if a removable drive wasn't unmounted before unplugging, the system wasn't properly shut down, some hardware error. What file system is on that drive? Windows file sytems should be checked from Windows.

---

### Post by Hasimir on 2017-10-03
This is the output from mount.
The last line in bold is the HDD that I use to store everything. It's a logical partition, both my file systems (Ubuntu and Win10) are in a different HDD.

```

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8129260k,nr_inodes=2032315,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1630976k,mode=755)
/dev/sdb6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=888)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/sdb1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/120 type tmpfs (rw,nosuid,nodev,relatime,size=1630972k,mode=700,uid=120,gid=127)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1630972k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
**/dev/sda1 on /media/hasimir/DATA type fuseblk (ro,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)**

```

I'm trying to follow these instructions ( [https://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/](https://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/) ) but with no visible result. When I run **mount** again I get the same "ro" string.

---

### Post by Hasimir on 2017-10-03
The sda1 partition is NTFS
I tried this solution but it did not work.
This is the output of the operation...

Mounting volume... The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.

---

### Post by Hasimir on 2017-10-03
Found this thread about a similar problem.
[https://ubuntuforums.org/showthread.php?t=2341841](https://ubuntuforums.org/showthread.php?t=2341841)

Apparently the latest Windows10 update reset some stiings to their default state, including the trice damned "Fast Startup" option.
Turning that off solved the problem instantly :)

---

### Post by Impavidus on 2017-10-04
That's a known problem with recent Windows versions. Glad you solved it.

---

