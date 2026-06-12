---
title: "Swap Partition not used after this mornings kernel update"
date: 2006-07-12
forum: General Help
---

### Post by ahaslam on 2006-07-12
Hi there,

I got a few system updates this morning, including a kernel update.
The only thing that's never worked on my laptop in Dapper is the hibernate function. I just tried to hibernate, to see whether the kernel update has addressed the issue and was met with the following: 
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

### Post by MellonCollie on 2006-07-12
I don't know enough to say if something's wrong, but my system shows the same things as yours. Hopefully someone more knowledgeable will come along and comment soon. :)

---

### Post by ahaslam on 2006-07-12
> **MellonCollie said:**
> I don't know enough to say if something's wrong, but my system shows the same things as yours. Hopefully someone more knowledgeable will come along and comment soon. :)
Did this also occur following todays updates?

Tony.

---

### Post by MellonCollie on 2006-07-12
> **Anthony Haslam said:**
> Did this also occur following todays updates?


I can't answer that because I hadn't checked this out before today's updates. ](*,)

---

### Post by jmeadows111 on 2006-07-12
I'm seeing the same thing, using 686 version of kernel.

---

### Post by ahaslam on 2006-07-13
I'm using kernel: 2.6.15-26-k7 (but reverting doesn't help).

This is the second time that updates have borked my system, remember the login box with autologin last month? Updates should fix bugs, not create them. 


Tony.

---

### Post by ahaslam on 2006-07-13
**I reworded my  title on a new thread and got a fix:** ;) 

> **Paerez said:**
> have you tried reformatting the swap?
```
# sudo mkswap /dev/hda3
# sudo swapon /dev/hda3
```
Thank you, that worked perfectly. :) 

Thanks again,

Tony.

---

