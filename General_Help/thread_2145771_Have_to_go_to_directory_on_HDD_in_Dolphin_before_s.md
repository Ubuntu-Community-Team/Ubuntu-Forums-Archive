---
title: "Have to go to directory on HDD in Dolphin before starting application  from HDD?"
date: 2013-05-16
forum: General Help
---

### Post by vivienneanthony on 2013-05-16
Hello

I'm having a recurring problem. Whenever I power on my system and start Ubuntu 12.04. I have to start Dolphin and go to a directory in my primary HDD not my primary SDD. Ubuntu then recognizes the directory or drive in terminal or Dolphin. Since I have to start apps they do not run until I do this.

Do anyone know what might be going on or how to fix it?

Viviennehdd

---

### Post by Impavidus on 2013-05-16
That sounds like your HDD isn't automatically mounted. [This]("https://help.ubuntu.com/community/Fstab") is how it can be solved.

If not clear at once – which I can imagine – can you post the result of the command```
mount
``` both directly after boot and after you have accessed the HDD? And give the output of```
cat /etc/fstab
```

---

### Post by vivienneanthony on 2013-05-16
I copied the fstab and mount information. This is after I reboot and went into Dolphin then selected the HDD. The SDD card works fine.

This is the current fstab file

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc  proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=2e4c5480-5537-4e77-b593-3cd5722438d6  /      ext4  auto,defaults             0  1  
# swap was on /dev/sda5 during installation
UUID=279cd14e-13eb-4efa-bb80-8ec32e60f695  none   swap  sw                   0  0  

The mount says the following

/dev/sdb1 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/vivienne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vivienne)
/dev/sda1 on /media/home2 type ext4 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by Impavidus on 2013-05-16
Your hard disk, known to Linux as /dev/sda1, is not automatically mounted during boot. When going there in Dolphin it is automatically mounted at a location known as /media/home2. To be able to access the drive before going there in Dolphin you need to make an entry in /etc/fstab telling Linux to automatically mount the drive at boot. Make a backup of that file, open it with root permissions and add a line to it to mount /dev/sda1. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The line will look something like this:
```

UUID=01234567-89ab-cdef-0123-456789abcdef /my/mountpoint/ ext4 defaults 0 0

```
Make sure your mountpoint exists. You may need to tweak the options.
To get the UUID of your drive, use this command in a terminal:```

ls -l /dev/disk/by-uuid/ | grep sda1

```

---

### Post by vivienneanthony on 2013-05-16
Thanks. It was a obvious solution to the problem. Thanks for highlighting it.

---

