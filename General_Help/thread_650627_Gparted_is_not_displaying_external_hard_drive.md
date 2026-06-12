---
title: "Gparted is not displaying external hard drive"
date: 2007-12-26
forum: General Help
---

### Post by onesojourner on 2007-12-26
I am trying to reformat a couple external drives but Gparted is not displaying them. Is there something special I need to do?

---

### Post by TidusBlade on 2007-12-26
not sure if this is neccesary, but is the External HD mounted?

---

### Post by RudolfMDLT on 2007-12-26
I take it that it's a USB drive? plug out the drive and issue the following command in the terminal: "lsusb" then plug the drive in and issue the command again. Do you see the drive in the list?

---

### Post by louieb on 2007-12-26
May be something simple. Did you check the drop down box in the upper right hand corner?

---

### Post by LaRoza on 2007-12-26
> **louieb said:**
> May be something simple. Did you check the drop down box in the upper right hand corner?

I was thinking that too.

It doesn't display all devices, only one at a time.

---

### Post by Kegir on 2008-04-23
I'm having the same problem, I've tried it on a couple different computers with two different laptop sata drives.  And no its not in the drop down, only the internal drive shows up.

command ls usb: cannont access usb: No file or directory

---

