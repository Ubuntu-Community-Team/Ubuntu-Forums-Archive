---
title: "Need a walkthrough unmounting windows"
date: 2007-10-09
forum: General Help
---

### Post by jrharvey on 2007-10-09
I Just wanted to make sure I was doing the right thing and not mess up. I want to permenantly unmount my windows vista and recovery from Ubuntu. After typing this (gksudo gedit /etc/fstab) I get this line of stuff. I wanted to know what i do from here because I would really like to not ruin anything. When I looked at other post people said to remove all windows stuff and then some people said not to remove at all so Im a little confused.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=406EC89E6EC88E5A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=18aaedea-e445-4a8a-9a2a-71d149b3879e /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=19793c60-c124-44f6-ab15-b5ee66f5e1cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by LaRoza on 2007-10-09
> **jrharvey said:**
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=406EC89E6EC88E5A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=2C88743C8874071C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=18aaedea-e445-4a8a-9a2a-71d149b3879e /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=19793c60-c124-44f6-ab15-b5ee66f5e1cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Just comment it out, with a #. I did it in the quote for you.

---

### Post by thirddeep on 2007-10-09
Put a hash '#' in front of the two lines that has ntfs in it.

This way, Ubuntu will no longer mount them, but you did not delete anything.

Thd.

---

### Post by jrharvey on 2007-10-09
Ok I rebooted and it did not remove the windows partitions. Any sugguestions?

---

### Post by LaRoza on 2007-10-09
> **jrharvey said:**
> Ok I rebooted and it did not remove the windows partitions. Any sugguestions?

Do you want the Windows partitions themselves removed, or do you want them to not be mounted at start up, i.e. no icons on the desktop?

---

### Post by jrharvey on 2007-10-09
I DO NOT WANT TO REMOVE THEM. I UNFORTUNATELY need them. I just want to remove them from ubuntu. Oh and yes, I did save after I added the #'s

---

### Post by jrharvey on 2007-10-09
I would love the icons to be removed and not mount them at startup

---

### Post by thirddeep on 2007-10-09
Type in :
```
sudo mount
```
and paste the output here please.

Hard to imagine that those partitions will be mounted if they are commented out.

Thd.

---

### Post by jrharvey on 2007-10-09
I will post a pic tooo. The icons changed but they are still there.



/dev/sda7 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda5 on /media/sda5 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdf1 on /media/MY IBOOK type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

---

### Post by LaRoza on 2007-10-09
They will still be in the computer windows, but unmounted. Try to access one, you'll have to give a password.

Cool theme, by the way.

---

### Post by thirddeep on 2007-10-09
That is likely Gnome VFS that picks the partitions up.  I would not know how to tell Gnome VFS to ignore partitions.

But as LaRoza said, they are unmounted.

Thd.

---

### Post by jrharvey on 2007-10-09
Ah thank you very much. I am still transitioning to from mac as you can see. Anyways, is there no way to remove the icon???

---

### Post by jrharvey on 2007-10-09
ok well that is fine. If as long as I cant accidently mess up the partition thats all that really matters.

---

