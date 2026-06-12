---
title: "Deleted files still taking up space"
date: 2015-05-25
forum: General Help
---

### Post by johny why on 2015-05-25
Hi 

Sorry for posting this in 'General', was not sure where to post. 

On a new Gnome install, my data hard drive (not the gnome install drive) showed about 5GB free. 

then i deleted about 10GB. Now my hd is showing only 3GB free!

i browsed to Trash, and i could not browse to Trash-- got error described here:

[http://askubuntu.com/questions/137832/trash-folder-not-showing-files](http://askubuntu.com/questions/137832/trash-folder-not-showing-files)

[http://askubuntu.com/questions/507173/cannot-remove-file-from-trash-that-was-put-there-as-root](http://askubuntu.com/questions/507173/cannot-remove-file-from-trash-that-was-put-there-as-root)

After updating gnome, i am not getting error when i browse to trash. But, still only 3GB free. 

Since i deleted over 10GB, this cannot be correct. How can i fix?

thx!

---

### Post by Elfy on 2015-05-25
check this out

[http://ubuntuforums.org/showthread.php?t=898573&p=5649417#post5649417](http://ubuntuforums.org/showthread.php?t=898573&p=5649417#post5649417)

---

### Post by johny why on 2015-05-25
hi, thx!

i checked all the dirs listed in that post, and found my trash folder in /.Trash-0

but, there was only a small 15MB folder in .../files. Did not find the ~10 .iso files i just deleted, worth ~10GB. Drive still showed 3GB free. The other dirs in that article turn up nothing. 

Finally found my stuff in /media/jack/MyStuff/.Trash-0. Good thing the article told me to search, but might be helpful if the article said "this is not a complete list. You must do a search if you don't find your deleted files in these folders." I almost didn't bother searching, because i thought, 'well if this is a complete list, then why bother searching"'

btw, i noticed i still get error when trying to open the Trash in nautilus. 

ps, was actually 25GB worth of deleted files!


thx!

---

### Post by coffeecat on 2015-05-25
> **johny why said:**
> 
Finally found my stuff in /media/jack/MyStuff/.Trash-0.

It sounds as though you deleted your files with a root-owned nautilus. That's a recipe for making life difficult for yourself. Was there a reason for this?

---

### Post by johny why on 2015-05-25
Indeed. I installed gnome ubuntu from the Live CD. That gnome ubuntu installer created this account, and i went with it. i assumed, incorrectly apparently, that the installer would walk me through creating all necessary accounts. 

So, i was supposed to create a restricted or user account right after the install?

thx!

---

### Post by coffeecat on 2015-05-25
> **johny why said:**
> Indeed. I installed gnome ubuntu from the Live CD. That gnome ubuntu installer created this account, and i went with it. i assumed, incorrectly apparently, that the installer would walk me through creating all necessary accounts. 

So, i was supposed to create a restricted or user account right after the install?

thx!

This doesn't answer my question. Let's go back one step. How did you open nautilus when you deleted all those files that ended up taking up space?

Edit: Oops - missed the links in your first post. You were opening nautilus with "sudo nautilus" or gksudo nautilus". Why did you think you needed to do this?

---

### Post by johny why on 2015-05-25
sudo nautilus

i did sudo because i'm unable to write to this disk without sudo.

thx!

---

### Post by coffeecat on 2015-05-25
> **johny why said:**
> 

i did sudo because i'm unable to write to this disk without sudo.


Then that is your underlying problem. Why don't we sort that out for you? Having a drive that you can only write to as root is inconvenient to say the least, and could lead you to do things which might compromise your desktop security - such as opening a file browser with root permissions.

My guess is that your drive is formatted ext3/ext4 and that the filesystem is owned by root. It's an easy thing to fix. Plug the drive in, let it be mounted, and post the output of these commands:

```
sudo fdisk -l
mount
```

---

### Post by johny why on 2015-05-25
> **coffeecat said:**
> My guess is that your drive is formatted ext3/ext4 and that the filesystem is owned by root.
i  created the partitions on a different OS as root (Puppy linux, which does everything as root). 
It's the internal HD, not external. Formatted ext2.
Been researching how to set up permissions without success. Appreciate the help.

```
jack@boombox:~$ sudo fdisk -l
[sudo] password for jack: 

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0003a72b

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1           2048  19533297  19531250   9.3G 83 Linux
/dev/sda2       40962048 976773119 935811072 446.2G 83 Linux
/dev/sda3       39010302  40962047   1951746   953M  5 Extended
/dev/sda4  *    19533824  39008433  19474610   9.3G 83 Linux
/dev/sda5       39010304  40962047   1951744   953M 82 Linux swap / Solaris

Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order.
```

```
jack@boombox:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1954232k,nr_inodes=488558,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=393072k,mode=755)
/dev/sda4 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=393072k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```

---

### Post by coffeecat on 2015-05-25
Your data partition - which I assume is sda2 - is not mounted, unless you accidentally omitted a line from the end. I assume you are mounting this from nautilus. Please mount the partition and then re-run the mount command and post the output.

---

### Post by johny why on 2015-05-25
sorry 'bout that! forgot i still have not added the partition to fstab (is there a gnome gui for auto-mounting internal partitions?)

```
jack@boombox:~$ sudo fdisk -l
[sudo] password for jack: 

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0003a72b

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1           2048  19533297  19531250   9.3G 83 Linux
/dev/sda2       40962048 976773119 935811072 446.2G 83 Linux
/dev/sda3       39010302  40962047   1951746   953M  5 Extended
/dev/sda4  *    19533824  39008433  19474610   9.3G 83 Linux
/dev/sda5       39010304  40962047   1951744   953M 82 Linux swap / Solaris

Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order.
```

```
jack@boombox:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1954232k,nr_inodes=488558,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=393072k,mode=755)
/dev/sda4 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=393072k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda2 on /media/jack/MyStuff type ext2 (rw,nosuid,nodev,relatime,uhelper=udisks2)
```

---

### Post by coffeecat on 2015-05-25
> **johny why said:**
> sorry 'bout that! forgot i still have not added the partition to fstab (is there a gnome gui for auto-mounting internal partitions?)

Let's not complicate things just at the moment. There's a simple command to change the ownership of all your files and the ext2 filesystem below. Then we can look at how you mount the partition. There is no GUI that I can recommend apart from what you are doing at the moment with nautilus. But it's easy enough to add a line to fstab manually once we've sorted out ownerships.

First &#8211; open a root nautilus with gksudo nautilus and delete the .Trash-0 folder and all contents. I don't think it matters if we change the ownership of that from root, but it might as well be got out the way, as you probably won't need one in the future. Once you've done that, from a terminal:

```
sudo chown -R jack: /media/jack/MyStuff
```

Now test the partition. Are you now able to drag and drop copy stuff into it from an ordinary (not root) nautilus?

**Edit:** Also, post the output of:

```
sudo blkid
```

And I'll help you with a fstab line for sda2.

---

### Post by johny why on 2015-05-25
> **coffeecat said:**
> delete the .Trash-0 folder and all contents. I don't think it matters if we change the ownership of that from root, but it might as well be got out the way, as you probably won't need one in the future.
need one what? and why 'probably'?

> **coffeecat said:**
> ```
sudo chown -R jack: /media/jack/MyStuff
```
thx for that, but i found that command already, and elected not to. i feel making one user the owner is not the right approach for me. i access this partition from multiple OS's, which is why i use a separate partition for data files instead of putting them in Home dir. i do not use Home. Also, i may create new users on this OS which i would like to have access to that partition automatically. So that is why i don't want to give jack ownership of the partition. 

therefor, my plan was to give some group full access to the partition-- a group that all non-root users are automatically part of anyway. "users", i think? i did not yet figure out how to give a group read/write access to the partition. 

then i noticed the default account (jack) was part of an administrator group, and i don't want to use the machine as admin for daily use (why is the default account an admin? seems unsafe).

therefor, my plan was to create a new non-admin account for daily use (after i figured out how to give a group read/write access to the partition). 

then i noticed jack was no longer an admin, but is now "custom". No idea what it means yet, or how that happened, or what to do about it, but i don't like it. Haven't figured that out yet.

```
jack@boombox:~$ sudo blkid
[sudo] password for jack: 
/dev/sda1: LABEL="os2" UUID="65600c91-b1bc-40fd-a890-ce3d665c96f9" TYPE="ext4" PTTYPE="dos" PARTUUID="0003a72b-01"
/dev/sda2: LABEL="MyStuff" UUID="20bcdb5c-e5bb-4f0c-bc74-4aef7ac74770" TYPE="ext2" PARTUUID="0003a72b-02"
/dev/sda4: LABEL="puppyos" UUID="4174d51e-a7a6-47af-941f-d04541b34570" TYPE="ext4" PTTYPE="dos" PARTUUID="0003a72b-04"
/dev/sda5: UUID="ca3bcd5c-d70d-49a7-8cae-646dd95fc93e" TYPE="swap" PARTUUID="0003a72b-05"
```

> **coffeecat said:**
> I'll help you with a fstab line for sda2.
Really appreciate that, but i already know how.

sorry this topic has gone in a whole different direction than the OP.

THX!

---

