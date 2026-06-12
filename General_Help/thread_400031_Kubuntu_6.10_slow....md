---
title: "Kubuntu 6.10 slow..."
date: 2007-04-03
forum: General Help
---

### Post by wizzkid on 2007-04-03
Hi guys,

I would need help... Ive been using the new version of Kubuntu which is 6.10 edgy for about 4 to 5 months now, then I noticed that my system becoming slow.. why is it? when i first install it, its fast, but now, it became slow... below is my fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0

# /dev/hda2 -- converted during upgrade to edgy
# Root Partition
UUID=19c0c3fc-c5ff-4403-be5b-cb4bafa18303 / reiserfs nouser,defaults,atime,auto,
rw,dev,exec,suid 0 1

# /dev/hda3 -- converted during upgrade to edgy
# Boot Partition
UUID=9f119fec-6f02-428f-a158-d9cf08b9a06b /boot ext3 nouser,defaults,atime,auto,     rw,dev,exec,suid 0 2

# /dev/hda5 -- converted during upgrade to edgy
# Home Partition
UUID=93ea947a-1da9-4c3e-8236-529f1282aad3 /home reiserfs nouser,defaults,atime,a     uto,rw,dev,exec,suid 0 2

# /dev/hda6 -- converted during upgrade to edgy
# Swap Partition
/dev/hda6 none swap sw 0 0

# /dev/hda7 -- converted during upgrade to edgy
# Data Partition
UUID=447B-0C43 /media/data vfat iocharset=utf8,umask=000,uid=0,gid=0,auto,rw,nou     ser 0 0

/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0


Any help, would be highly appreciated.

Thanks....

---

### Post by acormack on 2007-04-03
When it is running slowly you need to look at which running processes are taking the most cpu.

You can either do this via top

sudo top on a command line 

or by

System, Ksysguard from the menu.

If the system sometimes seems to run OK then I would try to compare the processes when it is slow and when it is OK.

---

