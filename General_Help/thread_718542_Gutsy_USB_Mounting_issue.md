---
title: "Gutsy USB Mounting issue"
date: 2008-03-08
forum: General Help
---

### Post by depointer on 2008-03-08
in the last 2 weeks i have encountered an issue where on my acer 5100 laptop My built in media reader has started working but it has disabled all usb function other then external mouse and keyboards,  Is anyone aware of a work around to get this working as i can not get my ipod, external usb hard-drive or external usb dvd rw to mount at all. they are not even showing as detected in an lsusb, and the kernel gives a message that there is a problem with the usb cable?

as a subnote, is there a way to backdoor reinstall via external usb, my internal dvd drive is dead, and when trying to load the ubuntu install disks on live cd it brings me to shell prompt, on alternate, it says it fails to load the cdrom / can not detect the cdrom after booting to that point.


please forward an email with any suggestions to [email]tuxteronline@gmail.com[/email]

---

### Post by depointer on 2008-03-08
i am in worse shape now, after installing some packages i now have no networking, no desktop, no device capabilty, if anyone has a way to get the external dvd/cd drive to mount please let me know asap.

---

### Post by depointer on 2008-03-08
Any suggestions at all would be appreciated, I have tried everything i can think of to make this work.

---

### Post by ODF on 2008-03-08
Maybe they are disabled in the bios. If lsusb can't see them ... i can't tell anymore =(

---

### Post by depointer on 2008-03-09
not disabled by bios, currently the usb cdrom is detected by bios, it boots, and during the boot process it goes into 'Stupid mode' saying that there is no cdrom attached, i am suspecting that the system loads it and thinks its an idea/ata drive instead of being usb. maybe there is a specific init paramater that will work to help?

---

