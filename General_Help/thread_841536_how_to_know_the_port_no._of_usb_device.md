---
title: "how to know the port no. of usb device ?"
date: 2008-06-26
forum: General Help
---

### Post by dexter.deepak on 2008-06-26
i have connected my nokia phone with my computer and 'lsusb' gives the output:
Bus 001 Device 002: ID 0421:04b9 Nokia Mobile Phones

when i used my dial-up usb modem, i tried i had /dev/ttyACM0 as the port no. for it ...but i cant find the port no. of this device.

---

### Post by Taxman415a on 2008-06-26
The last few lines of dmesg a bit after you attach the device might give you what you want. Try dmesg |tail in a terminal. Also it may try to auto mount it as a mass storage device so try looking at the output of mount and see if something new has shown up. Use umount to unmount it.

---

