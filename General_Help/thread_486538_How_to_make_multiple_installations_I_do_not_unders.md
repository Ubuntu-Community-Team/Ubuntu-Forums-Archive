---
title: "How to make multiple installations? I do not understand the guide ..."
date: 2007-06-28
forum: General Help
---

### Post by mcp97 on 2007-06-28
I followed these steps in the guide:

>    1.      Do a normal installation,
   2.      Rename C:\wubi\disks\system.virtual.disk into something else (say ubuntu.virtual.disk)
   3.      Reinstall, say using kubuntu ISO
   4.      Rename system.virtual.disk to kubuntu.virtual.disk. So you should now have C:\wubi\disks\ubuntu.virtual.disk and C:\wubi\disks\kubuntu.virtual.disk
   5.      Edit C:\wubi\grub\menu.lst:
          *            Comment out the hidemenu option (put a "#" in front of it, so that the menu is displayed)
          *            Increase the timeout time (how long the menu is displayed before selecting the default option)
          *            copy the last block starting with "title". Each title block is a boot menu entry
          *            Give an appropriate title to each of the 2 blocks (e.g. "title Ubuntu" and "title Kubuntu")
          *            Add the kernel paramter "root_img=ubuntu.virtual.disk" to the first block and "root_img=kubuntu.virtual.disk" to the second one.

Where do I have to add the kernel parameter? In a separate line? At the end of the kernel line? I tried different ways, but my installations hang everytime I try to boot one.

This is an example of what I tried:

> title Ubuntustudio
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro root_img=ubuntustudio.virtual.disk
initrd /wubi/boot/initrd
boot

Where do I have to insert 

> root_img=ubuntustudio.virtual.disk

and what do do with the parameter "setup_iso=ubuntu-7.04-alternate-i386.iso"? Replace it with "setup_iso=ubuntustudio-7.04-alternate-i386.iso" or something like this? I tried this too, but the system would not boot too.

Can someone show me please how the block has to be?

---

### Post by ago on 2007-06-28
The best way is to install Ubuntu and then use synaptic to install the other desktop packages, for instance for xubuntu, all you have to do is install Xubuntu-desktop. Then when you login in the option you choose the desktop environment that you prefer.

---

### Post by mcp97 on 2007-06-28
Thank you very much for your answer. The guide states exactly what you said, but nevertheless I would really prefer to have two separat installations. So I'm still trying to figure out how the block has to look. :-k

---

### Post by ago on 2007-06-28
kernel /wubi/boot/linux find=/wubi/boot/linux quiet splash ro system_virtual_disk=ubuntustudio.virtual.disk

sorry forgot to update the guide

---

### Post by mcp97 on 2007-06-28
Nothing to worry. I am very happy because it worked now. Many thanks!

---

