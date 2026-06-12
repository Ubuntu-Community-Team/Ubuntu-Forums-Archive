---
title: "Dual boot ext HD"
date: 2008-06-16
forum: General Help
---

### Post by bizarrechaos on 2008-06-16
I have been trying to install ubuntu on an external hd, and everything goes good, it installs and reboots, at reboot it loads straight into windows xp, no GRUB I dont think it is writing to the MBR can someone help me

I might add i had to do a manual fixmbr awhile back when i had ubuntu on another ext hd that crashed

---

### Post by Het Irv on 2008-06-16
If you are installing Grub to the External Hard Drive you need to do one of two things, either set up your computer to boot to USB (assuming the External is connected through USB), or you can use a Grub disk to restore Grub to the main internal drive.  I think setting up your computer to boot to USB would be the eaisiest way, its just a small change in BIOS.

---

### Post by bizarrechaos on 2008-06-16
so do i just boot up hit f12 and change the boot order so that the usb drive is at the top

---

### Post by meierfra. on 2008-06-16
> so do i just boot up hit f12 and change the boot order so that the usb drive is at the top

Yes.

But, for example if you  have a dell, you have hit f2 to permanently  change the boot order

---

