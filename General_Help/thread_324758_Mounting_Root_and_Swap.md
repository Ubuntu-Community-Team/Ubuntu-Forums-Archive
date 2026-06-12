---
title: "Mounting Root and Swap"
date: 2006-12-24
forum: General Help
---

### Post by Manuito on 2006-12-24
Hello,

I'm running Kubuntu 6.10 from an external USB disk.

I found out that, according to System Settings / Advanced / Disk & Filesystems, my Kubuntu ext3 partition and the swap are not mounted during system start (it says they are Disabled).

Anyway I am using Kubuntu without problems (so I think the ext3 partition must be actually mounted) and, according to *# free*, swap is also working correctly (maybe they are automatically mounted because they are considered as a external storage, I don't know).

I discovered that using FSTAB I can Enable these two paritition in the Disk & Filesystems screen, but only works using /dev/XXX or LABEL= (it doesn't work using UUID).

The only problem I get if I don't mount my ext3 partition that way (or at least the only problem I've seen to the moment) is that I can't monitor the free and used disk space of the root partition.

Should I mount these two partitions anyway??

I don't want to mount swap using /dev/sdb5 in FSTAB because I do want to change my external drive from one computer to the other. UUID is also not working. Is there a way I could assign a LABEL to the Swap partition ???

Thanks!!

---

### Post by Manuito on 2006-12-24
I think I could solve my problem if someone solves this one:

Can I assign a LABEL to the swap partition??

I used Partition Magic in Windows and saw that the swap partition has the label "SWAPSPACE2", but when I try to use it in FSTAB it doens't work.

Is there another way to call the swap in the fstab appart from UUID= and /etc/XXX ???

Thanks!!

---

