---
title: "hd1 or hd0"
date: 2008-05-31
forum: General Help
---

### Post by Stolea on 2008-05-31
How can I tell if my windows partition is on hd1 or hd0?

---

### Post by tamoneya on 2008-05-31
post the result of ```
sudo fdisk -l
```From there I can tell you which one it is.

---

### Post by labinnsw on 2008-06-01
Try this command. 

sudo gedit /boot/grub/menu.lst

Look for windows in the file, then close without editing.

---

