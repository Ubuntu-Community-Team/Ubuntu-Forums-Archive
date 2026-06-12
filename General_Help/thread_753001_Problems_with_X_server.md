---
title: "Problems with X server"
date: 2008-04-12
forum: General Help
---

### Post by dropscience on 2008-04-12
I installed Ubuntu Studio a while ago and first i only got this message when i was booting studio but now i get it when booting Ubuntu too. The message i get looks something like this, this is after Ubuntu tries to perform a automatic system check: automatic file system check (fsck) of the root file system failed. Could not start X server due to an internal error. The root file system is currently mounted in read only mode.

Then i says that i need to perform a system maintainance. 

Can somebody help me? would be very grateful!

---

### Post by PmDematagoda on 2008-04-12
Boot the Live CD and then when you reach the desktop post the outputs of:-
```
sudo fdisk -l
```
and
```
cat /etc/mtab
```

---

### Post by dropscience on 2008-04-12
Ok thanks :)

---

