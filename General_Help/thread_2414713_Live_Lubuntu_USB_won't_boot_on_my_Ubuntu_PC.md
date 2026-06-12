---
title: "Live Lubuntu USB won't boot on my Ubuntu PC"
date: 2019-03-14
forum: General Help
---

### Post by dblack49 on 2019-03-14
* I have a 64-bit pc with 16 GB RAM and 2 TB hard disk
* The operating system is Ubuntu 18 LTS
* I have a live 32-bit Lubuntu USB (that is L-ubuntu) that won't boot.
* I also have a live 64-bit Ubuntu USB which boots happily using this live-usb-stick.
* It (the same 32-bit Lubuntu USB stick) does not work on a friend's windows 10 pc.
-------------------
* I wonder what the problem is?  I wanted the 32-bit so that I could use the usb-stick on other (old) pc's - do you think it is this - the fact that it is 32-bit?
Thank you for your help.

Thank you for your time and expertise.
Duncan

---

### Post by sudodus on 2019-03-14
The problem might be that the computer boots in UEFI mode, and most 32-bit systems boot only in BIOS mode (alias CSM alias legacy mode).

If you create a persistent live drive with mkusb and select 'usb-pack-efi' at the settings menu, your Lubuntu 32-bit USB drive will boot also in UEFI mode.

But if you want to boot also with 'secure boot', you need a Lubuntu 64-bit system.

Links:

[help.ubuntu.com/community/mkusb/](https://help.ubuntu.com/community/mkusb/)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by dblack49 on 2019-03-14
Thank you VERY much - this does sound like the problem.  I am a little slow so will only attempt this correction when I have some time over the weekend and will then post an update.  Once again, thank you very much for your time and expert help.
Sincerely
Duncan

---

### Post by sudodus on 2019-03-14
You are welcome and good luck :-)

---

### Post by Impavidus on 2019-03-14
Computers that only boot 32 bit OSs are very unlikely to boot in UEFI mode. Have you actually tried to boot your 32 bit Lubuntu live disk on a computer that needs 32 bit?

---

### Post by mastablasta on 2019-03-14
what is the boot error?

how did you create the USB?

---

