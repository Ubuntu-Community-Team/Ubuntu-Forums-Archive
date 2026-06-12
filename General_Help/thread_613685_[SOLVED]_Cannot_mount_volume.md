---
title: "[SOLVED] Cannot mount volume"
date: 2007-11-15
forum: General Help
---

### Post by kdarkentity on 2007-11-15
This is the error i get whenever i insert my usb drive.

unable to mount the volume 'usb-vault'

details
mount: wrong fs type, bad option, bad superblock on /dev/sdf1 missing codepage or helper program,
or other error in some cases usesfull info is found in syslog -try dmesg tail or so

---

### Post by erikringmar on 2008-02-23
bumping this.  I have the same problem.

---

### Post by CoryLuLu on 2008-04-15
i have the same problem but it was after my power went out, restarted and my slave drive says it cannot mount

---

### Post by JayStapleton on 2008-04-15
Is your thumb drive encrypted?  Do you need a password to use it under Windows?

Does it work in any other Linux or Windows machines?

---

### Post by jellyman on 2008-04-30
I suddenly developed this problem in Feisty.  I got the error message saying it was unable to mount one of the volumes on my usb hard drive.
HERE IS MY SOLUTION:  Launch GPARTED, right click on the volume that can't be mounted and select the mount option.  Gparted will mount the volume for you and it will be accessible from the operating system.

Simple, quick and effective.  This works for me whenever the error occurs.

---

