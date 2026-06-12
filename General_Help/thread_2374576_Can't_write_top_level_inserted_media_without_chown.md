---
title: "Can't write top level inserted media without chown"
date: 2017-10-17
forum: General Help
---

### Post by kazakore on 2017-10-17
If I insert a USB key or other external drive I can not write to the top level. If it already has files and a folder structure on it I can usually edit (add/remove etc) files that exist below the top level, but I can not add files or folders to the top directory of the drive. This is true even when the device has just been formatted with GParted and not even removed from the system inbetween! Therefore there is no other possible place to add files, nothing on the device and clearly not the way it should be!!

I can run a command just as "chown -R myname /media/myname/device" and then I can write to the top directory.

Why is media getting mounted with root as the owner and making it unusable for my normal login?

I think it does occasionally work, if I restart the system and try and insert a piece of media first thing I do. Obviously I'm not going to want to restart my PC every time I want to insert an external device!!


Ubuntu Studio 16.04.

---

### Post by Impavidus on 2017-10-17
How have you formatted the usb drive? If it's fat32, ntfs or some other file system that doesn't support UNIX permissions, your /media/username/device should be owned by you. If it's a filesystem that does support UNIX permissions, /media/username/device will be owned by whoever is the owner according to information on the usb drive. Directly after formatting that would be root, but if you change that using chown, the new owner should be retained after removing and reinserting the drive.

---

### Post by kazakore on 2017-10-17
FAT32 so that it can be read across different computer systems as need be. Still seems to make the most sense for external drives and sharing media to me, despite its downfalls.

As you say it should be mounted with me user as the owner and instead it's seems to be mounted as root. At least at the top directory/mount point.

Obviously my user profile has root permissions but that is not the same as me being the root user.

---

### Post by ajgreeny on 2017-10-17
With the USB freshly plugged in let's see the output of ```
ls -l /media
mount
```

---

### Post by kazakore on 2017-10-17
```
$ ls -l /media/
total 4
drwxr-x---+ 4 root root 4096 Oct 17 12:34 user


$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=7887360k,nr_inodes=1971840,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1581920k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=11219)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,noatime)
/dev/sda6 on /media/user/Data type ext4 (rw,noatime,nodiratime,errors=remount-ro,data=ordered)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1581920k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
/dev/sdb1 on /media/user/DBCC-47F4 type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)


```

---

### Post by kazakore on 2017-10-17
Looks like the I need to change to owner of /media/user right??


EDIT:

Changed owner to my user, chmod to =777 for /media/user and reinserted.

Now I still can not write to the top directory of the inserted media, so operationally nothing has changed.

```
~$ ls -l /media/user/
total 36
drwxrwxrwx 11 root root  4096 Oct 14 18:15 Data
drwxr-xr-x  3 user user 32768 Jan  1  1970 DBCC-47F4

```

So ls is showing me as being the owner and group owner now.

If I right click or look in Thunar is shows me a X on the directory and in Permissions says that root is still the owner.


Why should these two ways of checking permissions/owner disagree with each other?

---

### Post by Morbius1 on 2017-10-17
You don't want to mess with the permissions of /media/user because of this:
> drwxr-x---[COLOR=#0000cd]**+**[/COLOR] 4 root root 4096 Oct 17 12:34 user 
You didn't create that folder. The system did. And when it does that it sets up an acl ( access control list ) which is what the little **[COLOR=#0000cd]+[/COLOR]** sign is all about.

I don't know what it will show now but had you run this command before you did your chown you would have seen something like this:
> getfacl /media/morbius
getfacl: Removing leading '/' from absolute path names
# file: media/morbius
# owner: root
# group: root
user::rwx
[COLOR=#0000cd]**user:morbius:r-x**[/COLOR]
group::---
mask::r-x
other::---
Root is the owner of that folder not you but root allows you and only you the ability to traverse the folder to get to what is under it. This is by design.

I suppose if Linux was really serious about this security feature it would prevent the user from doing what you did.

---

### Post by kazakore on 2017-10-17
Ahhh fair dos I admit I completely missed that plus sign.

Changed owner user and group back and reset permissions to 750. Everything looks and seems the same as before...

Still showing the owner as being root when I check with Thunar, and thus not letting me create or delete files, whereas it shows as being owned by my user when checking through the command line.

---

### Post by kazakore on 2017-10-18
Hmmm strangely at the end of yesterday I noted it was only doing this with one USB key now. The other day I had it affecting every media I tried, three different USB keys and more than one hard drive but installed in the same caddy....

---

