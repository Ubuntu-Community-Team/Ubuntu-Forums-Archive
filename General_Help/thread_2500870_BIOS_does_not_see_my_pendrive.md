---
title: "BIOS does not see my pendrive"
date: 2024-09-14
forum: General Help
---

### Post by raleigh3 on 2024-09-14
I used BalenaEtcher to install Ubuntu 24.01 to a pendrive.

I went into the BIOS to change the boot order, but it does not see the pendrive? (SDC)

I checked to make sure the sha256 sum was correct.

---

### Post by yancek on 2024-09-14
Did you verify the downloaded iso of Ubuntu?  Did you get any warning/error messages when writing the iso to the USB?  Do you have another computer you can use to attempt to boot from the USB to eliminate that as a potential problem?

---

### Post by Rubi1200 on 2024-09-14
You could also try using Rufus and make sure it is set for UEFI mode.

Sometimes, writing in dd mode also helps.

---

### Post by raleigh3 on 2024-09-14
Thanks. 

It is installed and it has the boot flag set. But my BIOS still does not see it?

---

### Post by yancek on 2024-09-14
I've never used it or Etcher but the  Ubuntu site recommends Rufus as also suggested in post 3 above.   Have you tried that? 

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

>  It is installed and it has the boot flag set. But my BIOS still does not see it? 		

What does that mean?  Are you unable to boot an Ubuntu iso you have written to a usb drive.  Do you mean you can see the data on the usb from another OS?  Do you have options to boot UEFI as well as Legacy in your BIOS and have you tried both?

---

### Post by 1fallen on 2024-09-14
Dang I've used BalenaEtcher for years with "0" issues, Nor with mkusb

---

### Post by oldfred on 2024-09-14
Some UEFI require you to turn on allow USB boot, or full USB support or similar setting.

---

