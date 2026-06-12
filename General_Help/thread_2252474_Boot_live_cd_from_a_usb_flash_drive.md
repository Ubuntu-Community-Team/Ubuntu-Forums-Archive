---
title: "Boot live cd from a usb flash drive"
date: 2014-11-12
forum: General Help
---

### Post by jimmyh1972 on 2014-11-12
Hi - I have a win 8 installed on my computer & also a customized ubuntu (a little bit ols version) which I frequently use
the CD is old and can't boot because it doesnt support UEFI & Secure boot options also I dont want to change BIOS settings because I use both a few times in a day
is there a way to boot the CD with a help from Ubuntu 14.04.01?
that s becaues the old CD is realy realy necessary
thank's ahead - Jimmi

---

### Post by yancek on 2014-11-12
What is the CD used for?  Is it a bootable CD on a flash drive?  What is on it?  If it is some type of bootable CD, then to boot it you need to set the boot priority in the BIOS so the flash drive is first.   I don't have UEFI so I don't know what the settings are but I would think there would be a simple way to change boot priority to boot the flash drive then change it back again, maybe not?

---

### Post by sudodus on 2014-11-12
I suggest you try with a virtual machine. Install VirtualBox and boot it from the old bootable CD. (It would also work, if you clone it to an ISO file and boot the virtual machine from the ISO file.)

---

