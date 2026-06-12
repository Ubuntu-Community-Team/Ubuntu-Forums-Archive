---
title: "How to remove Grub from mbr and install it on /partition side ?"
date: 2004-10-29
forum: General Help
---

### Post by fm78 on 2004-10-29
Hello ubuntu users

I have installed Ubuntu on my  computer and I choosed to install Grub on MBR. but I want to replace it with Acronis Boot manager as I can remove it directly from windows in time of need.

How can I remove Grub from MBR and install it on partition hda6 ?

I am scared to use fdisk /mbr .

Do I have to use a live cd like Mepis for that ?

Thanks people

---

### Post by jdong on 2004-10-29
First, install grub onto a partition.

Primer on GRUB numbering: /dev/hda1 is (hd0,0). /dev/hdb2 is (hd1,1) and so on.

run **sudo grub**. Issue the following commands:

```

root (hdX,Y)
setup (hdX,Y)

```

Where root is the device with the /boot/grub folder and setup is the partition you want to install on.

Then , you **must** use fdisk /mbr or fixmbr to restore a Windows MBR!

---

