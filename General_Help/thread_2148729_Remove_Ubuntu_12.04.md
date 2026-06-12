---
title: "Remove Ubuntu 12.04"
date: 2013-05-26
forum: General Help
---

### Post by Bresser on 2013-05-26
I have Ubuntu and Mint dual booted. I want to get rid of Ubuntu how do I do that. Linux Mint 14 and Ubuntu 12.04. They are on same harddrive.

---

### Post by 2F4U on 2013-05-26
Read through these (swap Ubuntu and Mint, if necessary):

[http://askubuntu.com/questions/84669/removing-os-from-dual-boot-computer-and-recovering-hd-space](http://askubuntu.com/questions/84669/removing-os-from-dual-boot-computer-and-recovering-hd-space)
[http://ubuntuforums.org/showthread.php?t=2143173](http://ubuntuforums.org/showthread.php?t=2143173)

---

### Post by Dennis N on 2013-05-26
> **Bresser said:**
> I have Ubuntu and Mint dual booted. I want to get rid of Ubuntu how do I do that. Linux Mint 14 and Ubuntu 12.04. They are on same harddrive.

Here is a basic outline of what can be done as I see it. Assumes you have an MSDos partition table.
Plan carefully. Use caution. The ultimate responsibility is yours. 

1) Be sure that Linux Mint is the OS that installed the bootloader to the MBR. If not, run grub-install from Mint, being sure to install to the MBR, then update-grub. Check that booting process works OK after that.
2) Format the Ubuntu partition (assumes no separate home partition).
3) Boot into Mint (at this point, Ubuntu would still be on the grub menu).
4) Run update-grub to build a new grub.cfg without Ubuntu.
5) Reboot.

---

