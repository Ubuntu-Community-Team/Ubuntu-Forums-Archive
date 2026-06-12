---
title: "hp deskjet 3323 USB printer"
date: 2008-05-20
forum: General Help
---

### Post by worldy on 2008-05-20
So,how do i set up my HP deskjet 3323 on ubuntu gutsy ? :(
Its a USB printer.

---

### Post by gavinjb on 2008-05-20
Hi,

I would suggest you try [http://openprinting.org/printer_list.cgi?make=HP](http://openprinting.org/printer_list.cgi?make=HP)

But I can only see entries for the 3320 and 3325, it might be worth looking at these and see if they work with your printer.

---

### Post by worldy on 2008-05-20
Thanks.

:(
But seems my printer is not working.
lsusb is not detecting the printer even after a plugged-in re-boot.
Also found that the required drives and software (HPLIP) comes bundled with ubuntu.

I cudnt even switch the printer on by pressing it. What was i thinking
:mad:

---

### Post by gabhla on 2008-05-20
Try :

sudo hp-setup

Worked for me.

---

### Post by worldy on 2008-05-20
With sudo hp-setup,it exits with

error: No devices found.
error: Error occured during interactive mode. Exiting.

---

