---
title: "Problem - No Swap - What's Happened"
date: 2006-07-13
forum: General Help
---

### Post by ahaslam on 2006-07-13
Hello,

Sorry for posting this twice, but I haven't received any help and thought I needed to reword the title. Here it goes:

I got a few system updates yesterday, including a kernel update (2.6.15-26-k7).
While trying to hibernate I was met with the following: 
```
swsusp: could not find swap partition try swapon -a.
```
Trying "sudo swapon -a" returns: "swapon: /dev/hda3: Invalid argument"

After logging back in I checked my fstab and it seems ok to me:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
I looked at the system monitor, it also showed that the swap partition was not in use:

[ATTACH]12610[/ATTACH]

Here's what the disk manager shows for the swap partition:

[ATTACH]12611[/ATTACH]

My swap partition was on previously. Has anyone else experienced this problem? Does anyone have a solution?

As always, all comments & suggestions are greatly appreciated.


Tony.

PS. Changing back to the previous kernel does not help.

---

### Post by Paerez on 2006-07-13
have you tried reformatting the swap?
```
# sudo mkswap /dev/hda3
# sudo swapon /dev/hda3
```

---

### Post by ahaslam on 2006-07-13
> **Paerez said:**
> have you tried reformatting the swap?
```
# sudo mkswap /dev/hda3
# sudo swapon /dev/hda3
```
Thank you, that worked perfectly. :) 
Any idea why I needed to do this, it was working a couple of days ago?

Thanks again,

Tony.

---

### Post by Paerez on 2006-07-13
I dunno. My guess is that they changed the way swap is in the kernel, and it got a little disgruntled. (this is my way of saying I have no idea what happened, and I got a lucky guess right)

:D

---

### Post by ahaslam on 2006-07-13
Thanks anyway, I really appreciate your help.

Tony.

PS. "flatulent ferret" - lol :)

---

