---
title: "[SOLVED] External Removable drive hogged by windows"
date: 2007-12-22
forum: General Help
---

### Post by Nunu on 2007-12-22
When I connect my external drive to my pc and try to access it I get an error saying that the drive is used buy windows. I have tried the safely remove hardware wizard in windows and reconnected it to my Ubuntu 7.10 PC but still get the same thing. Any ideas?

---

### Post by heatpumpcontrol on 2007-12-22
plug drive back into a Windows pc and run a chkdsk /f /e ----> if e is the drive letter of the drive. This might fix it. Or you can use Partition Editor and right click on the usb drive and tell it to perform a check

---

### Post by Nunu on 2008-01-07
CHKDSK seemed to have done it, looks like it is working on ubuntu now , thanks

---

