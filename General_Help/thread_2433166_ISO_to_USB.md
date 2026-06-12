---
title: "ISO to USB"
date: 2019-12-14
forum: General Help
---

### Post by freddy58 on 2019-12-14
What Program in the Ubuntu world would you use to burn an ISO that I have sitting on a Hard Drive in my computer, to a USB Thumb Drive plugged into my Computer?  It would be nice if could Format the USB Thumb drive also.

---

### Post by guiverc on 2019-12-14
I personally use `dd`, but I'd not recommend it for anyone (there is no safety net, I've wiped a hdd using it because of a careless typo).

Instead I'll point you to documentation.
(if you go into Ubuntu Software, there is software that burns to multiple devices too)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0)

and I find always worthwhile, after your write  (note: CD refers to any media inc. thumb-drives)
[https://help.ubuntu.com/community/CDIntegrityCheck](https://help.ubuntu.com/community/CDIntegrityCheck)

---

### Post by c0n7r4 on 2019-12-14
If you are running Mint, try:

$ mintstick -m iso

It's a nice GUI for iso to usb writing.

---

### Post by C.S.Cameron on 2019-12-15
Mkusb creates either a Live or Persistent USB that boot either with BIOS or UEFI.
[https://www.debugpoint.com/2019/10/how-to-create-persistent-usb-ubuntu-linux-mint/](https://www.debugpoint.com/2019/10/how-to-create-persistent-usb-ubuntu-linux-mint/)

---

### Post by Artim on 2019-12-15
MintStick also formats USB drives.

---

