---
title: "can't see hebrew files in ubuntu 7.1 on wubi"
date: 2007-11-22
forum: General Help
---

### Post by [THE] KILLER on 2007-11-22
Hi,

I have a problem with hebrew files on my ntfs, I can't see them.
Normally I know how to fix this problem, by adding "nls=utf8" in the fstab file, but since wubi created the ntfs mounting I'm not sure what to do, I don't understand how the mounting is taking place.
this is my fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,defaults,errors=remount-ro 0       1
/host/ubuntu/disks/home.disk /home           ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/host/ubuntu/disks/boot /boot none bind 0 0

``` 

And this is my mount table:
```

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/home.disk on /home type ext3 (rw,loop=/dev/loop1)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=adam)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

10x, Adam.

---

### Post by ago on 2007-11-22
see if remounting /host with the desired option addresses the issue.

---

### Post by [THE] KILLER on 2007-11-22
Haven't  succeeded, can u plz give me the exact command?

10x, Adam.

---

### Post by ago on 2007-11-22
try editing /etc/init.d/mounthost

change the line:

mount -n -o remount,$hostopts,$hostmode $host_device /host 

to>>

mount -n -o remount,nls=utf8,$hostopts,$hostmode $host_device /host 


(requires reboot)

---

### Post by [THE] KILLER on 2007-11-22
Still didn't do the trick...

But I think it's the right direction.

Adam.

---

### Post by [THE] KILLER on 2007-11-25
Hi,

Any other ideas that might solve the problem? I realy want to keep using wubi but as long as this problem exist I'm forced to use vista :(

10x.

---

### Post by ago on 2007-11-26
You can try to replace casper in initramfs-tools/scripts. I'll give you more detailed instructions later on (not on my pc now).

---

### Post by [THE] KILLER on 2007-11-27
replace casper? 
my usr/share/initramfs-tools/scripts/casper-premount folder is empty.

can u give a more detailed explanation plz?

10q.

---

### Post by ago on 2007-11-29
in fact there may be an easier way. Edit /boot/grub/menu.lst and add the boot option

rootflags=nls=utf8

To the first line beginning with "kernel"

---

### Post by [THE] KILLER on 2007-11-30
Still no good,
I don't understand how can it be?! I have no problem seeing hebrew files in other partitions. But the partition with the wubi on it that loads to /host/ just won't.

I'm getting desperate :(

---

### Post by ago on 2007-11-30
Can you check whether nls had any effect in cat /proc/mounts?

---

### Post by [THE] KILLER on 2007-11-30
I don't see any effect, but here it is:
```

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/disk/by-uuid/D824464E24462FB4 /host fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/loop0 / ext3 rw,data=ordered 0 0
/dev/loop0 /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/loop1 /home ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/D824464E24462FB4 /boot fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev 0 0

```

---

### Post by [THE] KILLER on 2007-11-30
Another thing that might help, I have been trying to do the mounting manually like this:

```

sudo mount /dev/disk/by-uuid/D824464E24462FB4 /host2/ -o  nls=utf8

```

And like this:

```

sudo mount /dev/disk/by-uuid/D824464E24462FB4 /host2/ -o  nls=iso8859-8

```

And like this:

```

sudo mount /dev/disk/by-uuid/D824464E24462FB4 /host2/ -o  utf8=true

```

And I still got the same thing, my drive without my hebrew files and folders.

---

### Post by [THE] KILLER on 2007-12-11
Hi,

Any new thoughts about the problem before I'm giving in and installing without wubi?

Adam.

---

