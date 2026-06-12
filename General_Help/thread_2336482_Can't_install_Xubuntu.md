---
title: "Can't install Xubuntu"
date: 2016-09-08
forum: General Help
---

### Post by den4ik1996 on 2016-09-08
Hi.

It is not the first time I am dealing with Linux based operating systems.. Usually I would download an iso file and create bootable Live USB , and then I restart my computer and I am offered to install a new OS. I did exactly the same thing for Xubuntu this time, but when I reboot my laptop nothing happens, it just logs me back to my current OS. Why?

---

### Post by Keith_Helms on 2016-09-08
Either it doesn't see your USB drive as bootable or your laptop is not configured to boot from the USB drive.  First thing to do is reboot and go into the bios and check your boot devices and boot order.  If boot from USB is enabled and comes before boot from hard drive, then your thumb drive is probably not formatted correctly.

---

### Post by yancek on 2016-09-08
You need to set the boot priority in the BIOS to boot from the usb or it will boot from the hard drive.  Have you done that?
What operating system(s) do you have on the computer now, if any?  Are you using UEFI?

---

### Post by den4ik1996 on 2016-09-09
I just went to Boot Options and did everything from there. Thanks anyway!

---

### Post by yancek on 2016-09-09
If I'm reading your post correctly, you have previously used a usb drive to boot and install some version of Linux on this computer.  Possible problems are a bad download which you can check by doing an md5 checksum to verify it.  You can try booting from the usb on another computer if one is available to see if the usb works.

---

