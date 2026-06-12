---
title: "[SOLVED] How to Stop Unique CD/DVD Mount Naming"
date: 2008-06-11
forum: General Help
---

### Post by kennyrogersjr on 2008-06-11
This is directed toward the more technically savvy UNIX/Linux users...

I want my CD/DVD drives to have a static mount name. Whenever I insert a disk into either drive, they come up with the disk name as the mount point.

Examples:

```
/dev/scd0 /media/NFSUDISK1
/dev/scd1 /media/NFSUDISK2
```

What I want is:

```
/dev/scd0 /media/cdrom0
/dev/scd1 /media/cdrom1
```

Instead of cdrom0 I could use scd0. I choose cdrom0 because those are already present in my system, however they are not being used.

I have spent a couple hours already parsing through Google, my Linux commands book and even the 'man mount' pages. I just can't find anything related.

There is a what-if. I can live with the unique disk names if there was a way for me to fix my multi disk install problem. I keep getting the repetitive 'insert disk 2' pop-up.

OS specs:

```
Ubuntu 8.04 (Kernel 2.6.24-18-generic)
```

Here is my /etc/fstab output:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=61f802f3-da99-4e46-9177-d6b2619d1a30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1CC4E3D5C4E3AEE8 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=3f0665fc-6c03-4e05-96ad-e6b6168de7be none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

tmpfs /dev/shm tmpfs defaults,ro 0 0

```

Thanks,



Ken

---

### Post by kennyrogersjr on 2008-06-12
bump

---

### Post by prshah on 2008-06-12
> **kennyrogersjr said:**
> T
I want my CD/DVD drives to have a static mount name.

What I want is:
```
/dev/scd0 /media/cdrom0
/dev/scd1 /media/cdrom1
```

Instead of cdrom0 I could use scd0. I choose cdrom0 because those are already present in my system, however they are not being used.

```
[color=red]/dev/hdb[/color]        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
[color=red]/dev/hda[/color]        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```



What your describe is how ubuntu handles CDs/DVDs by default. Eg, irrelevant of the CD volumename, the CD is mounted only at /media/cdrom0, _not_ at /media/volumename. But the name displayed on the desktop will be the volumename of the CD.

However, if that is not the behavior you are getting, your fstab may be at fault; you have some strange entries. By your own admission, you have scd0 and scd1, but the fstab reserves "/media/cdrom0" and "/media/cdrom1" directories for /dev/hda and /dev/hdb. Maybe you need to change the /dev/hda and /dev/hdb to /dev/scd0 and /dev/scd1. For reference, it should look like this:
> ```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

Note with the above entries, your root owned and root grouped /media/cdromX directories will take a new owner and group when the CD/DVD disc is mounted.

---

### Post by kennyrogersjr on 2008-06-12
> **prshah said:**
> 
Note with the above entries, your root owned and root grouped /media/cdromX directories will take a new owner and group when the CD/DVD disc is mounted.

Should I be wary? Is this different from the norm, or should my user have the appropriate rights instead of root?

Good idea, I thought of that first, but I doubted myself.

Thanks,



Ken

---

### Post by kennyrogersjr on 2008-06-12
Thank you so much. This fixed both my problems.

For summary purposes, I no longer have dynamic directories whenever I pop in a CD/DVD. The corresponding drives open to either /media/cdrom0 or /media/cdrom1. I'll change it later to a different name when I feel like it. My other problem was fixed when my directory didn't change when I was installing a multi-disc program. The installer proceeded to recognize the second disc and install the program.

I'll list the steps I took to solve my issue.

> 1. Open a terminal window
2. type **sudo gedit /etc/fstab**
3. Original output:
[INDENT]a. This is just an example, do not paste over your own fstab!
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=61f802f3-da99-4e46-9177-d6b2619d1a30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1CC4E3D5C4E3AEE8 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=3f0665fc-6c03-4e05-96ad-e6b6168de7be none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

tmpfs /dev/shm tmpfs defaults,ro 0 0
```[/INDENT]
4. New output:
[INDENT]b. Change your original to the bolded device below. Again DO NOT PASTE OVER YOUR OWN FSTAB!!!
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=61f802f3-da99-4e46-9177-d6b2619d1a30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1CC4E3D5C4E3AEE8 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=3f0665fc-6c03-4e05-96ad-e6b6168de7be none            swap    sw              0       0
/dev/**scd0**        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/**scd1**        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

tmpfs /dev/shm tmpfs defaults,ro 0 0
```

(Thanks to prshah for pointing out the obvious.)[/INDENT]

5. Restart two times. 
[INDENT]a. I restarted the first time and both my drives "acted funny". So I restarted another time and both are back to normal. Make sure you restart, not logout![/INDENT]


Thanks again.



Ken

---

