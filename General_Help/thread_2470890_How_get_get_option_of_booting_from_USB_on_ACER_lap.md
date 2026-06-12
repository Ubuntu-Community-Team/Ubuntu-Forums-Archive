---
title: "How get get option of booting from USB on ACER laptop/stuck on grub command line."
date: 2022-01-15
forum: General Help
---

### Post by tomsax on 2022-01-15
Hi,

I had ubunto and windows on dual boot on an ACER laptop which my son is using.

Something has gone wrong and it is now gets stuck on the grub command line on start up.

I want to boot from a windows repair USB drive but in BIOS I can't seem to set the laptop to try booting from usb. It just gives option of booting from either ubuntu or windows boot manager, and neither of those work going straight to grub.

Not sure what I can do.

Happy to just reinstall windows as my son never uses ubunto but can't even do that.

I have disabled secure boot in Bios and from googling stuff it seems I need to choose legacy boot mode rather than UEFI boot mode.  But I have apparently no option of changing boot mode.  It is just greyed out.  I think I may have to change SATA mode but can't find the way of changing the SATA mode.  I think I found before that there is some magic key to press and then I get options for SATA mode, but can't remember what that is.

Tom

---

### Post by tomsax on 2022-01-15
Oh seems I should have tried windows manager with the usb boot repair in the socket!  Boot repair now running but it has been about an hr just scanning the drive...

---

### Post by tomsax on 2022-01-15
Well I have solved the problems of not booting from usb, but I still can't solve the problem of it being stuck on grub.  The boot recovery disk didn't work as it just kept searching and searching but then just got stuck in that state.

---

### Post by tomsax on 2022-01-16
Now solved by using a windows repair disk and installing winddows newly over everthing...Only solution that worked for me.

---

### Post by dragonfly41 on 2022-01-16
It might be safer to leave your son to use Windows and for your interest in Ubuntu purchase an external SSD. But first make sure that Acer laptop offers a USB 3.0 port (not 2.0 which is slower). Ubuntu runs very well on an external SSD (USB 3.0). I recommend Crucial.com for supply of SSD. I have two in an external docking bay with own power supply but Crucial offers a portable SSD which draws on laptop power. Windows has an app Rufus which can create a Ubuntu installer.

---

