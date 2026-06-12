---
title: "Install Windows from Ubuntu"
date: 2007-03-15
forum: General Help
---

### Post by Kuroki on 2007-03-15
Hey im currently running Ubuntu and I want to dual boot (there are a few windows only programes i want to use) but im not shere how to get the dual boot to work without actually formatting my harddrive and starting with windows.  Every time i open the installer for windows it messes up and dose that annoying "close or debug" thing.  Anyone know how to help me?

---

### Post by peabody on 2007-03-16
Try using something like the Gparted CD to shrink your Ubuntu partition.  Google for the link.  Try to leave the first partition on the drive open for Windows if possible.

---

### Post by soaro77 on 2007-12-31
Does anyone know how this can be done? I have been running Ubuntu for a while and just bought a new hard drive and want to add Windows as a dual boot on the new hard drive. But I want to keep my current Ubuntu installation on my primary hard drive.

I can find tons of info on how to start with Windows to make a dual boot but I want to do it backwards and start with Ubuntu. How can this be done?

I really don't want to have to start over and install Windows first and lose all my Ubuntu installation if I can help it.

---

### Post by RC Howe on 2007-12-31
Doing it backwards is hard because Windows installs its own boot loader that erases grub. I have not tried this, but what I would recommend is resizing your ubuntu partition, installing Windows normally using the new partition, then installing grub again.

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)
for installing grub.

---

### Post by geirha on 2007-12-31
Why not just install windows in a virtual machine? Might be a bit slower, but you don't have to reboot every time you need to use your windows programs. [WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

---

