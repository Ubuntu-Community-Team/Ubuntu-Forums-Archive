---
title: "My backup drive has gone read-only :("
date: 2016-09-30
forum: General Help
---

### Post by coldraven on 2016-09-30
I thought that today would be a good time to do a backup and upgrade to 16.04. I have a 1TB Samsung external USB drive but when I plugged it in I could not create a new folder. The drive is several years old but is unplugged most of the time. It is about half full and formatted NTFS. 
Is there something I can try or should I just buy a new one?
What the heck are all these /dev/ram devices?, I have never seen those before. The external drive is /dev/sdb

I knew that I should not have read a news story today about exploding Samsung washing machines :(


```
sudo fdisk -l
[sudo] password for coldraven: 
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


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb1dec453

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 304455679 304453632 145.2G 83 Linux
/dev/sda2       304457726 312580095   8122370   3.9G  5 Extended
/dev/sda5       304457728 312580095   8122368   3.9G 82 Linux swap / Solaris




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xfc3203c1

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1          63 1953520064 1953520002 931.5G  7 HPFS/NTFS/exFAT


```

```
blkid
/dev/sda1: UUID="eeb0027a-2efa-4bf4-b59d-b28d5b213483" TYPE="ext4" PARTUUID="b1dec453-01"
/dev/sda5: UUID="8be11b51-f693-41e6-909f-564617656524" TYPE="swap" PARTUUID="b1dec453-05"
/dev/sdb1: LABEL="SAMSUNG" UUID="6405B83B1DF74416" TYPE="ntfs" PARTUUID="fc3203c1-01"


```

---

### Post by oldos2er on 2016-09-30
[This thread]("http://askubuntu.com/questions/703576/fdisk-l-shows-16-ram-disks-dev-ram0-ram15") explains the /dev/ram* devices.

Do you see any error when trying to create a new folder on the NTFS partition? What does the *mount* command say?

---

### Post by sudodus on 2016-09-30
Maybe it is mounted read-only. What happens if you unmount it and mount it read-write?

Maybe you have no permissions. Are you running the backup with superuser privileges? Can you write (copy) to the file with a simple sudo command line?

A system upgrade may have changed the default settings for external drives.

-o-

The following tip was made for a drive with a FAT32 file system, but I think it might work also for NTFS. They are both Microsoft file systems, and the permissions are set when mounted (and cannot be changed without unmounting and re-mounting).

Mount a FAT32 partition in a pendrive with read/write permissions for everybody:

(assumption: the pendrive is seen as /dev/sdx, replace x with the actual drive
letter, for example b: /dev/sdx1 ---> /dev/sdb1)

```
sudo mkdir -p /mnt/sd1  # only if you want a new mountpoint
sudo umount /dev/sdx1   # only if already mounted (but with bad permissions)

sudo mount -o rw,users,umask=000 /dev/sdx1 /mnt/sd1  # mount

echo 'Hello World' > /mnt/sd1/hello.txt  # test writing
cat /mnt/sd1/hello.txt                   # test reading
```

-o-

- Check the S.M.A.R.T. status, for example with 'Disks' alias gnome-disks. That should indicate if the drive is bad.

- Maybe the file system is bad. Check and repair it with Windows tools (in a DOS command line window)

```
chkdsk /f X:
```

or with a corresponding GUI tool. See this link: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by coldraven on 2016-10-01
> Check the S.M.A.R.T. status, for example with 'Disks' alias gnome-disks. That should indicate if the drive is bad.

- Maybe the file system is bad. Check and repair it with Windows tools (in a DOS command line window)

It does not show any SMART data but your second idea is good. I had forgotten that I actually have a working Windows box for the first time in years. It's a Win 8 laptop that I have dual booting with Ubuntu. I'll try to fix it later and get back with the outcome.

---

### Post by coldraven on 2016-10-01
@Olddoser
In Nautilus if I press ctrl+shift+N (new folder) I get an error message "Error when coping to SAMSUNG. The destination is read only"

```
mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1908800k,nr_inodes=477200,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=391828k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=391828k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb1 on /media/coldraven/SAMSUNG type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


```

---

### Post by coldraven on 2016-10-01
On  my other dual-boot laptop I used Windows to run chkdsk.
```
chkdsk /f E:
```
This seemed to find many errors and fixed them. Then I rebooted into Ubuntu and was able to copy files over.

Now I have plugged it into the laptop that I want to backup and the permissions have changed, it was owned by "Me" and now it's "Root". 
This is strange, I just ran```
gksu nautilus
```and right clicking the drive, selecting "Properties>Permissions" showed that I was the owner.
I quit root Nautilus and ran it as normal, doing the same thing shows the drive belongs to root :(

If I can do a backup I will do a fresh install on this laptop, both  it and me seem to be confused!

---

### Post by sudodus on 2016-10-01
Did you try to mount the drive according to the tip in post #3?

---

### Post by coldraven on 2016-10-01
> **sudodus said:**
> Did you try to mount the drive according to the tip in post #3?
No but I will try that tomorrow.

---

### Post by efflandt on 2016-10-02
Note that Windows partitions have no *nix like concept of permissions, so permissions depend upon mount options. However, if Linux detects problems with a partition (of any type) mounted read-write, it will automatically remount the partition read-only to try to prevent further damage.

I ran across that when I had a single Linux partition at the far end of my original 1 TB drive (no swap) following 3 existing partitions for Win7 (incl utility & recovery partitions). When I got into Linux steam and began filling up sda4 (where sectors are physically smaller near center of platters) I had times when I suddenly had no permission to write files to my home dir because the partition had auto remounted read-only. So I used Win7 to shrink its partitions before imaging them to a new drive and installing Linux on a larger partition. I also have a spare Ubuntu system on an old 80 GB SSD which is the drive grub is on, so I could repair the failing partition (including locking out badblocks) from there before getting around to replacing the drive.

---

### Post by coldraven on 2016-11-24
Sorry but I have had some problems. I will be away from home for the next month, hopefully by then I will be back on form.

---

