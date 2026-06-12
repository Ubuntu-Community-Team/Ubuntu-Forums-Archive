---
title: "cannot edit menu.lst file"
date: 2008-05-11
forum: General Help
---

### Post by ryehigh on 2008-05-11
hi all,

i was attempting to edit the menu.lst file through the terminal, and was unable to have it opened. when i attempted to edit it using the ABI and Mousepad applications, i was unable to save the changes i made. any assistance  would be greatly appreciated.

on a side note, i cannot get xubuntu to format a floppy drive nor to read from a floppy drive. any suggestions on this issue will be appreciated as well.

thank you!

[THIS ISSUE HAS BEEN RESOLVED]

---

### Post by Irony on 2008-05-11
Try nano;

```
nano /boot/grub/menu.lst
```

---

### Post by oldos2er on 2008-05-11
You need admin privileges to edit system files:

 sudo mousepad /etc/apt/sources.list

---

### Post by ryehigh on 2008-05-11
thank you to you both. 

Irony, your solution allowed me to edit the contents of the file, but i was unable to save the changes to the file.

oldos2er, your solution worked like a charm. thank you very much.

---

