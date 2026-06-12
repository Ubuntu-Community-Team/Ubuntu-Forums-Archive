---
title: "Dual-boot woes...."
date: 2006-08-06
forum: General Help
---

### Post by cleverselfreferentialname on 2006-08-06
Trying to install windows on the last partition of my hard disk as opposed to the typically advised first.

I have been trying to resize the ext3 root partition on my machine in order to gain enough space, but it won't work. Parted (I'm using gparted, but it spits out running commands in the terminal) complains that the partition size is bad. What could be a cause of this?

Assuming that it did resize correctly one time, I booted windows from the install CD and it complained that there is no hard drive. Right. I booted Kubuntu from my root partition again.

Linux and Windows both seem to be against me today. Usually I'm pissed at one or the other (more often the latter).

---

### Post by h00s on 2006-08-07
> **cleverselfreferentialname said:**
> Trying to install windows on the last partition of my hard disk as opposed to the typically advised first.

Windows must be installed to first partition.

Read this for solving all dual-booting problems: :) 
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by temcat on 2006-08-07
I've heard that with right options in Grub, you can hide the first partition with Linux and trick Windows into thinking that it's partition is the first one. I haven't researched or tried that however, and I may be mistaken.

---

