---
title: "gnu grub error?"
date: 2008-02-29
forum: General Help
---

### Post by chrisx16x2008 on 2008-02-29
restarted my computer because it was freezing and this came up...

GNU GRUB version 0.97(636k lower/ 1505216k upper)
[Minimal BASH-like edditing is supported, for first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]

grub>

i was messing around with linuxe live distros not to long ago but i dont want one linuxw on my comp right now how can i get to windows?  i tried doing the fdisk / mdr and fix/mdr but i only have a vista upgrade CD

---

### Post by louieb on 2008-02-29
What you have is the GRUB prompt. That means GRUB can't find its configuration file: /boot/grub/menu.lst

To get VISTA to boot (if VISTA is still there) you need to replace the code in the MBR to load the VISTA boot loader. Lots of ways.
Great how to here: [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

