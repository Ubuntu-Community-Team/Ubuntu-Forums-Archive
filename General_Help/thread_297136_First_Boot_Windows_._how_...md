---
title: "First Boot Windows . how? .."
date: 2006-11-10
forum: General Help
---

### Post by LordOfRings on 2006-11-10
hi there.. 

Recently I installed ubuntu 6.10 . 
In the dualboot screen  as default OS  has Ubuntu .. 
How can change to windows .? .

thanks .

---

### Post by taurus on 2006-11-10
Boot into Ubuntu, then edit /boot/grub.menu.lst and change the default value from 0 to whatever entry your Windows is.  It is more likely number 3 (fourth entry) so just count...  Open a terminal and type

```
sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Average Joe on 2006-11-10
You have to change your /boot/grub/menu.lst file. There is an entry in there saying:
> default   0
The 0 indicates the first entry in you boot menu (Ubuntu). So if you want Windows to be the default entry (e.g. 3 rows lower) you should change into:
> default   3
I am not sure if 3 would be the right value for you though. It depends on your boot menu.

---

### Post by .t. on 2006-11-10
Don't! Learn to use free software!

And remember; it's freedom to remove your freedom as well (but I'm not going to help you constrict yourself).

---

