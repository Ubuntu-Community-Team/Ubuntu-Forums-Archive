---
title: "GRUB cannot boot by UUID (?)"
date: 2007-07-09
forum: General Help
---

### Post by limaunion on 2007-07-09
Hi there, I'm trying to run a self-compiled kernel (2.6.22) with libata enabled for my PATA hard disks (I'm trying to switch from the old IDE drivers to libata). The problem is that for some reason I'm getting this error:

VFS: cannot open root device UUID=blahblah or unknown block (0,0)

Grub and fstab have the correct UUID for the root filesystem ,what's wrong here ? 
Thanks in advance!
JC

---

### Post by Kodfish on 2007-07-09
initrds. those are annoying, i know that they are the problem but i'm ot sure exactly how to fix them. post your /boot/grub/menu.lst?

---

### Post by limaunion on 2007-07-09
> **Kodfish said:**
> initrds. those are annoying, i know that they are the problem but i'm ot sure exactly how to fix them. post your /boot/grub/menu.lst?

I've never used initrd. This is my menu.lst:

title           Ubuntu, kernel 2.6.22-cfs-v19-libata
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-cfs-v19-libata root=UUID=e7eb89ec-30ad-40a0-b2b5-188d6220b30d ro vga=775 init=/sbin/bootchartd
quiet
savedefault

title           Ubuntu, kernel 2.6.22-cfs-v19
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-cfs-v19 root=/dev/hda2 ro vga=775 init=/sbin/bootchartd

The second one is how I usually configure my menu.lst when I use the old IDE drivers. Now that I want to switch to libata I configured the root=UUID and there is the problem, for some reason I'm getting the error previously reported. I'll try changing UUID for /dev/sdax and see what happends.

JC

---

