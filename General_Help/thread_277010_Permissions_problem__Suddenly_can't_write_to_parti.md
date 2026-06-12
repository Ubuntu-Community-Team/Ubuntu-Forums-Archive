---
title: "Permissions problem?  Suddenly can't write to partition."
date: 2006-10-13
forum: General Help
---

### Post by mjpatey on 2006-10-13
I have a FAT partition that's shared between Ubuntu and Windows, and many important files live there, including my Firefox config files (so my Ubuntu and Windows Firefoxes have all the same extensions, bookmarks, etc.)

Suddenly, Firefox doesn't work.  And, when I try to delete any files from the partition, I can't.  So I go in using gksudo nautilus, hoping to edit permissions.  The directory that links to the partition ("share") now appears with a "Lock" emblem over its icon.  And, though it says the partition is set to allow everyone to read, write and execute, I can't write (delete), even using sudo.

So just for kicks, I click on "File Owner" to change it to me instead of root.  It says I can't change the owner because the directory is on a Read-Only disk!  Other apps that use this partition can't save to it now, either.  This partition has been used for several months (up until this evening) as writable.

Does anybody know how I might make the partition stop acting like it's read-only?  I can't use Firefox anymore because its config files are there, and all other documents on the partition are now no longer editable.

Thanks for any help you may be able to provide!

-Mark

---

### Post by alexfittyfives on 2006-10-13
Hi,

Maybe the partition has been mounted read only. Can you post the output you get when you type mount in a shell?

---

### Post by mjpatey on 2006-10-14
Sure!  Thanks for the tip... it's "hdb3" here:

$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hdb3 on /media/share type vfat (rw,umask=000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda1 on /tmp/disks-conf-hda1 type ntfs (rw)

It seems to be set to read and write, if I'm reading the line correctly.  Does "umask=000" have any effect on its write-ability?

-Mark

---

### Post by taurus on 2006-10-14
What does your /etc/fstab look like?

```
more /etc/fstab
```

---

