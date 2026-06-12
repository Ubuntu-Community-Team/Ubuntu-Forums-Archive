---
title: "Create ISO from CD"
date: 2006-07-15
forum: General Help
---

### Post by nami on 2006-07-15
Hi

How do you create an ISO from a CD?  Ideally, I am looking for a program similar to WinISO on Microsoft Windows?

nami

---

### Post by jordilin on 2006-07-15
For instance, k3b

---

### Post by nami on 2006-07-15
Thanks!

---

### Post by Ramses de Norre on 2006-07-15
```
dd if=/dev/hdc of=~/file.iso
```
If your cd-rom drive is /dev/hdc and you want to write to ~/file.iso.

---

### Post by Jucato on 2006-07-15
If you're using Nautilus, it's even easier (because Nautilus has its own burning utility). Put in the CD in your drive, go to Places > Computer, right-click on the mounted CD-ROM, choose "Copy Disc...", and in the Copy Disc dialog box, choose File Image in the "Copy Disc to" dropdown list.

---

