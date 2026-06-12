---
title: "hp pavillion x360 m1 truoble with bootable USB"
date: 2016-08-17
forum: General Help
---

### Post by Gatorade on 2016-08-17
I'm trying to get this laptop to boot from a USB drive but it's not working.
I've used YUMI to create the bootable drive, and I've gone in and changed the boot priority order to USB first.

The computer doesn't boot to the Flash drive , though. It just goes into windows 10.
I also tried installing it on a micro SD, with an SD adapter , that didn't work either.


can anyone offer any suggestions as to why it's not working?

---

### Post by yancek on 2016-08-17
What operating system do you have on YUMI?   Did you verify the download(s) of your iso(s) by doing an md5 checksum?  Have you tried the usb on another computer to see if it works?

I would check various options in the BIOS as in some instances, you will see the option to boot a usb drive listed under hard drives in the BIOS.  Should show by the name of the device.

---

### Post by Sableyes on 2016-08-17
The x360 has a bizzare reordering of priorities from bios.

Instead of bios, turn the laptop on, press escape, then press f9 and select boot from USB.

---

### Post by Gatorade on 2016-08-18
I made the bootable USB again , this time using Universal USB installer, and it worked.
I can't get the grub menu , though. It goes directly to windows, unless I put the USB drive in again, at which point it loads the live image. 

I went through the install option , and it says ubuntu is already installed, so I just need to get the GRUB menu to give me the dual boot option.

I am also having trouble with it getting the wifi to work, and this laptop doesn't have an ethernet port to plug a cable into.

---

### Post by Gatorade on 2016-08-18
> **Sableyes said:**
> The x360 has a bizzare reordering of priorities from bios.

Instead of bios, turn the laptop on, press escape, then press f9 and select boot from USB.

F10 takes you directly to the BIOS page

---

### Post by Sableyes on 2016-08-19
Yes. I know. I was explaining how to boot from USB, for which, you do not need Bios.

---

### Post by Gatorade on 2016-08-20
I still ended up on the BIOS page, to select the boot order.

it's all good , :)

---

