---
title: "Mods to Ubuntu after install on USB HD(PLEASE HELP)"
date: 2007-10-09
forum: General Help
---

### Post by Guardian-Mage on 2007-10-09
Honestly, I have this small question. I can't get support anywhere. I just want to use Ubuntu!

Ok, I had installed Ubuntu 7.10 on my USB hard drive a little while ago. I installed GRUB to /dev/sda which 
I believe is my boot sector of the USB hd. Now I have modified my boot priorities and it boots to the USB but only comes up with a GRUB command line, no menu.

I did modify the GRUB list file, changing the bottom so Ubuntu was on device hd0, and windows on hd1, because GRUB is on the USB it thinks the usb is hd0.

Should I go back and change hd0 to sd0, or sd1, or whatever, or are their other files for me to modify?

---

### Post by jnorthr on 2007-10-09
take a look at this: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by Guardian-Mage on 2007-10-09
Thanks but if you read my post, I can boot to USB, I just can't install it to USB, I don't know how

---

