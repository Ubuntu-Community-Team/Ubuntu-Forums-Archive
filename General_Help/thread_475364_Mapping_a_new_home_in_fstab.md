---
title: "Mapping a new /home in fstab"
date: 2007-06-16
forum: General Help
---

### Post by SoulinEther on 2007-06-16
I was wondering... 

I seemed to have made a mistake during my install and I didn't mount a partition of my hard drive correctly.

I wanted this partition to be /home:

```
# /dev/sda3
UUID=f549406f-1f3b-4b50-bbba-c1e314baa070 /media/sda3     ext3    defaults        0       2
```

My worry is there won't be any directories there for users.... Is there a procedure I should follow? I seem to recall a program to make a home folder for someone, but will it take what my current settings are? Thus, should I back these up..? Will I first have to remove my /home directory from the main / root partition?

---

### Post by SoulinEther on 2007-06-16
Sorry guys, a little bit more google searching came up with the perfect solution for me:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I hope this helps anybody else in my predicament!

---

### Post by nbv4 on 2007-06-16
I'm trying to do this, but I'm stuck on the second command:

find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /mnt/newhome/

the error it gives me is:

cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

when -p is clearly there. If I try to change around the switches so it's

find . -depth -print0 | cpio -pvd &#8211;null &#8211;sparse /mnt/newhome/

it says too many arguments

EDIT: I figured out the problem. That blog turned the double dashes into one long dash. the command should be:

find . -depth -print0 | cpio -pvd --null --sparse /mnt/newhome/

---

### Post by nbv4 on 2007-06-16
OK, now i messed it up big time. My home directory was set up as /home/nbv4/[home stuff here]

but now it's just /home/[home stuff here]

How an I add that /nbv4/ back in there without messing up all the symlinks and crap?

---

### Post by Happy_Man on 2007-06-16
I would suggest [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome). Never failed for me, on a wide range of computers and settings.

---

