---
title: "HOW-TO: Grub, Windows, 2 Hard Drives"
date: 2007-06-15
forum: General Help
---

### Post by fredramsey on 2007-06-15
While there is a lot of info out there on how to install, fix, and use Grub in a dual-boot system with Windows XP, Vista, etc., many posts assume that you have Windows and Ubuntu installed on the same hard drive in different partitions.

I have two hard drives in my system, one dedicated to Windows, the other to Ubuntu. I struggled constantly with Grub and the MBR. I've seen many posts that include something like this:

grub> root(hd0,0)

grub> setup(hd0)

This works for one hard drive. Here's what finally helped me:

I found out that the command "**root(hdx,x)**" needed to be the drive and partition of where you have **Ubuntu Linux installed**, while the "**setup(hdx)**" needed to be your **Windows drive**!

So, in my system, I have Windows on drive 0, and Ubuntu on drive 1. So when I re-install Windows and need to put Grub back on, I boot with a Live CD, start terminal, and type "sudo grub". I then type:

grub> root(hd1,0)

grub> setup(hd0)

Again, in this instance of two hard drives, the root command sets where your Ubuntu Linux is installed, while the setup command writes Grub to the MBR of the Windows drive.

I hope this helps someone!

;)

keywords: grub error cannot mount 17 21 master boot record bootloader menu.lst

---

### Post by NICU on 2007-06-15
That's good info, I have used this guide - [http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp) many times to configure and fix my hard drives after reinstalling multiple distros.  Its mostly the same info, but a little more generic.

---

### Post by tehtrk on 2007-06-17
Thanks!

One problem, though.  There needs to be a space between the commands and the parameters for those that want to cut and paste, I.E. root (hd1,0) .

---

