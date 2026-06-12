---
title: "Unable to boot after changing graphics driver"
date: 2013-04-15
forum: General Help
---

### Post by Hellfish03 on 2013-04-15
Hi

I am running ubuntu 12.04 on my asus 1225b netbook. Everything was fine until I changed the graphics driver. Now I am unable to access my desktop, it just gets stuck on with the ubuntu logo and 5 orange dots. I have tried accessing a terminal here by pressing Alt + Ctrl + F1, but nothing happens. I have a ATI Radeon HD 6320 on board. 

Is there any way revert to the default driver through a live usb boot?

Thanks

Hellfish

---

### Post by ajgreeny on 2013-04-15
What did you change the driver from and to, and how did you do it?

If you can tell us what you have installed now it should be possible to start in recovery mode from the grub menu and remove the current driver.  The system should then in theory be able to boot using the open source radeon driver, and from there you can look into another proprietary driver if you want to.

---

