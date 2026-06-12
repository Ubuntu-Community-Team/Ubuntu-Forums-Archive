---
title: "[SOLVED] Prevent Grub from Looking for Missing Partitions"
date: 2008-05-24
forum: General Help
---

### Post by ciamele on 2008-05-24
I have two hard drives in my PC. I have Ubuntu 7.10 on my Western Digital drive, and 8.04 on the Maxtor. I'm trying to remove 8.04 from consideration when booting up (so I can reformat the drive).

I misunderstood a thread and deleted the 8.04 partitions on my Maxtor drive with Gparted (I have no desire to recover that data).

Now I get "Error 22" in Grub when booting the PC.

I was finally able to boot into 7.10 by using Super Grub.

Now I would like to edit Grub so that there are no traces of 8.10 and my PC will boot straight to 7.10 without errors or having to choose it from the menu.

Note: Since booting into 7.10 with Super Grub, I have not attempted to reboot.

Thanks in advance for your help!

---

### Post by cdtech on 2008-05-24
While in Ubuntu, do:

sudo fdisk -l to find the drive you want to boot to.

on a command line type:
sudo grub, this will give you the grub shell >

If the disk you want to install the MBR is sda* for instance, then type (at the grub prompt):
setup (hd0)

then type quit at the prompt to exit grub.

---

### Post by ciamele on 2008-05-24
Thank you cdtech, that worked perfectly!

---

