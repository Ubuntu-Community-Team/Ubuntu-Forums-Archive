---
title: "How do I remove a /boot partition without destroying everything??"
date: 2008-02-17
forum: General Help
---

### Post by jesushero on 2008-02-17
I have guided a friend through an Ubuntu installation and he is having some problems every now and then. I now have ssh access on his computer and I'm trying to see what's wrong. First thing I noticed that could be a cause of problems is that there is a 32 megabyte partition on the start of the sda drive, sda1, ext3 that is mounted as /boot. This according to df is 98% full. Is there a way of removing this partition? Were there files put there during installation? Is it safe to just remove it from fstab or would that mean that the computer won't start again?? One of the problems this is causing is that I can't install the rt kernel because I'm getting a "device full" message (he's using audio a lot so I think he would benefit from the rt kernel). Any ideas (especially tried and tested) would be appreciated! Thanks..

---

### Post by 444 on 2008-02-17
Just delete the oldest kernels. I think it filled up when new versions came out in the updates.

Another option is simply putting the kernel you want someplace else, like in /. You will have to tell grub where it is of course (both the path and which partition).

Completely removing the partition would require reinstalling grub onto the main partition, which could be tricky.

---

### Post by jesushero on 2008-02-18
From what I saw the rt kernel is like 180mb in size. Would 32mb still be enough for it in a /boot partition?

---

### Post by 444 on 2008-02-18
It's really 180mb? I'm talking about the kernel image and initrd image only here (about 10M), the modules don't go in /boot.

---

### Post by jesushero on 2008-02-18
Ok, I was lucky enough that he had an empty partition standing on his computer. So I just swapped the /boot with that on fstab after copying all the contents (32mb). The computer rebooted successfully and I installed the linux-rt package (all of this over ssh). I have just checked the current /boot now, and it is just a bit over 200mb!!! There's nothing but the kernel in there (and probably modules), but it was just an apt-get install linux-rt command, I didn't mess with it at all!! At least it works now.. I now have to figure out how to split this drive since the /boot now has 80gb of space (with only 200mb occupied).

---

