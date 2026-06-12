---
title: "Dual-boot Issue"
date: 2008-06-12
forum: General Help
---

### Post by druntar on 2008-06-12
Okay, I know I've made the biggest error in Linux history, but I've installed Ubuntu Hardy Heron, and then installed Windows XP. The reason I'm trying to dual boot is that I'm having problems with some of my PC games in wine. I've been able to get back into Ubuntu through following the directions to re-install GRUB. I've also added windows xp to the /boot/grub/menu.lst. The issue I'm having is that every time I boot windows, when I restart instead of GRUB, it goes right back to windows. I then have to load up the live cd, and use Gparted to set the linux partition to boot again. It's a huge pain. I'm still relatively new to linux, but capable of following directions. If anyone could help I'd really appreciate it.

---

### Post by trevelyan on 2008-06-12
is this a two physical hard drive setup? or is it one disk with two partitions?

if its two hard drives just go in your motherboard's BIOS settings and set the ubuntu drive as the first boot device (or second.. as long as its before the XP drive.)

---

### Post by pmlxuser on 2008-06-12
You can just boot from an ubuntu disk and reinstall grub, once that is  done everything will work fine. if case is not as trevelyan state

ie
harddisk case!= trevelyan

---

### Post by druntar on 2008-06-12
Single hard drive. Two partitions. I've reinstalled grub. Through piddling around I've narrowed down the issue. After I boot windows and restart to get back to linux I have to use gparted from the live cd to reset the linux partition to boot. Once I do that grub works again.

Here's a link to "sudo fdisk -ls"

[http://paste.ubuntu.com/19600/](http://paste.ubuntu.com/19600/)

And here's a link to "sudo gedit /boot/grub/menu.lst"

[http://paste.ubuntu.com/19601/](http://paste.ubuntu.com/19601/)

---

### Post by druntar on 2008-06-12
Okay, what's happening is when I boot into windows it's some how setting the system to boot from the windows partition. If I load up the Live cd and use gparted to move the "boot" flag from the windows partition to the linux one every thing works fine until I boot windows again.

---

### Post by druntar on 2008-06-12
I'M AN IDIOT!!!

Here's what I was doing wrong. When reinstalling GRUB I was issuing these commands.....

sudo grub

root (hd0,0)

setup (hd0,0)

I was reinstalling grub over and over to the same location!!!!

I fixed the problem by using the correct command of:

setup (hd0)

I hope someone else is aided by my idiocy. System is booting fine now. Now if I can just get winblowz to recognize my networking card I'll be able to fix all the other devices it doesn't recognize. Thanks for the help guys.

---

