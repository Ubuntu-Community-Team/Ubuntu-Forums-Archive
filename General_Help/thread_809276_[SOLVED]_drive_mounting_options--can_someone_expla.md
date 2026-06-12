---
title: "[SOLVED] drive mounting options--can someone explain?"
date: 2008-05-27
forum: General Help
---

### Post by frank_costanza on 2008-05-27
Hello,

I'm trying to mount a disk partition as /home under Hardy. I added the partition and mount location in /etc/fstab.  However, I've seen different posts with different recommendations for the mount options.

One post recommended to mount with 'defaults' for options. The other recommended 'nodev,nosuid'. I've looked at the man pages for mount, but the descriptions don't make a lot of sense to me.

Can anyone explain which options would be best for a /home partition?

Thanks!

Here's my current fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9ebb442c-375d-41b5-a6cd-c5b59fa9ea71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=d71e3051-6d33-430e-976d-dfc214c408f5 none            swap    sw              0       0
# /dev/sda3
UUID=450a19e9-d852-4f2f-80aa-3082bf6da0c2 /home           ext3    defaults        0       2

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by ibuclaw on 2008-05-27
For the general purpose of what you'll use the home folder for, the options you currently have will be very beneficial for a single user desktop (or a family computer) and won't need changing.

The other mount options availiable mainly just benefit systems with a large amount of users.

For example:
[LIST]
[*]noexec - This sets the mount to allow no execution of binaries and scripts.
[*]nosuid - Sets the mount so chmod and chown don't take effect on any files or folders.
[*]nodev - Ignores some filesystem specific ways of writing data to the filesystem.
[/LIST]
Personally, the above features would be brilliant if I were setting up a college or university server, useless otherwise.

Regards
Iain

---

### Post by frank_costanza on 2008-05-27
Great, thanks for the explanation!

---

