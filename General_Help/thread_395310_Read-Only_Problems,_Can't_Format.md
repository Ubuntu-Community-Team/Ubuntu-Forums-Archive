---
title: "Read-Only Problems, Can't Format"
date: 2007-03-28
forum: General Help
---

### Post by RaphaelFaunus on 2007-03-28
'Lo. I just installed myself a brand new copy of Ubuntu (And I've had a little bit of prior Linux experience), and I have deleted that blemish of a software, Windows, from my hard drive. I had a spare hard drive inside the computer at that time, and it contains important files and things like that.
The problem is, I've got it as a mount point, but I cannot access if I am not a Root. Furthermore, now that I've tried changing the permissions, I get "Read-Only" errors.
This drive contains important information - It's likely I made a helluva mistake for formatting it into a FAT file system. Any way I can retrieve this information, without, of course, formatting the thing?

---

### Post by Ocxic on 2007-03-28
mount the drive, and do a "sudo chmod +rwx" to the drive/mount point that should allow you to read the info, as for formating, the drive needs to be unmounted b4 you can so that.

---

### Post by RaphaelFaunus on 2007-03-28
> **Ocxic said:**
> mount the drive, and do a "sudo chmod +rwx" to the drive/mount point that should allow you to read the info, as for formating, the drive needs to be unmounted b4 you can so that.
Well, no, the problem is I CAN'T format. This same drive contains all of my important information, stuff I can't lose. All I need to do is open the hard drive and copy the information back to my root.

---

### Post by fanatik on 2007-03-28
Let me get this clear... You just want to copy the data from the disk, and once thats done you want to format it?

OK, so we need to know which drive it is:

sudo fdisk -l
mount
cat /etc/fstab

Can you pase the output of the above commands please.

James.

---

### Post by RaphaelFaunus on 2007-03-28
> **fanatik said:**
> Let me get this clear... You just want to copy the data from the disk, and once thats done you want to format it?

OK, so we need to know which drive it is:

sudo fdisk -l
mount
cat /etc/fstab

Can you pase the output of the above commands please.

James.
Mmkay.
Here's the result of "Sudo fdisk -:"

> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19080   153260068+  83  Linux
/dev/hda2           19081       19457     3028252+   5  Extended
/dev/hda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       15504   117210208+   7  HPFS/NTFS
root@rfaunus-desktop:~#  mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/SpareDrive type ntfs (rw,noexec,nosuid,nodev)


The drive name is "/Dev/hdb1," set up in the mount "/media/SpareDrive."
I'm not sure if thats exactly what you need to know.

Here's what I get when I terminal myself "Mount:"
> /dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/SpareDrive type ntfs (rw,noexec,nosuid,nodev)

Here's the results for "cat/etc/fstab:"
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=54b3bd51-5e04-4214-a5a1-019279aba0f4 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5
UUID=f92c09f8-482d-451a-9679-57ed1ce4022c none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb1 /media/SpareDrive auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/hdb1 /media/SpareDrive auto users,atime,auto,rw,nodev,noexec,nosuid 0 0

Right, I'm not sure if I misunderstood what you told me to do. That's all I've got, though. Thanks.

---

### Post by RaphaelFaunus on 2007-03-29
Bump, because I'm really starting to need these files.

---

### Post by fanatik on 2007-04-20
Hi Sorry for the delay :(

So in your /etc/fstab there are 2 entries for /dev/hdb1 - really should only be one, but hey-ho it seems to have mounted ok.

I'm surprised it shows as r/w in your mount command since it looks as if you are just using the normal ntfs driver, which I thought was read only, or perhaps only r/w experimentally. the ntfs-3g driver has better r/w support.

anyway, can you not now just copy the files from /media/SpareDrive to say your /home dir?

$ mkdir /home/<username>/newdir
$ cp -pr /media/SpareDrive /home/<username>/newdir

I take it that doesn't work? how about if you run it as root?

$ sudo cp -pr /media/SpareDrive /home/<username>/newdir

then chown the files in newdir:

$ sudo chown -R <username> /home/<username>/newdir

Let me know how you get on.

James.

---

