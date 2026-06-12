---
title: "Problem with grub boot"
date: 2007-04-26
forum: General Help
---

### Post by gammaknife on 2007-04-26
Hi everyone. 
My problem is the following: I've recently resinstalled grub and received the following prompt:

grub >

, then I looked at [http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025) in order to solve my problem. I was able to mount the most recent kernel I had on the filesystem, then I saw a black screen with many processes and programs starting (  [xxxxxxxx,xxxxxxx] filename  ), then everything seemed to stop. I see a weird prompt:   (initramfs)                 and I've got absolutely no idea what to do...     I notice I'm able to use regular shell commands to go into directories and so on (I'm able to see the filesystem) but I'm not able to start X or whatever

I hope someone can help me

---

### Post by gammaknife on 2007-04-26
I've just been able to solve my problem, sry to have posted this message.

I had forgotten to enter information about the root partition at the
kernel /boot/vmlinuzxxxx  root=xxxx         line

---

