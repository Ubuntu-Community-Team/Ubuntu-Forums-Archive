---
title: "Change of starting OS"
date: 2008-04-26
forum: General Help
---

### Post by amazoohwawa on 2008-04-26
can anyone tell me how to change the starting OS among the ubuntu choices when I hit the esc button when the Ubuntu loads. basically i would like the third choice to always start rather me having to hit esc every time and making the choice manually!

help is always appreciated:)

---

### Post by tamoneya on 2008-04-26
you need to edit /boot/grub/menu.lst.  You should see a line that says ```
default 0
```or something similar.  This tells GRUB which OS to boot.  It is index at 0 so 0 -> first item.  You should change yours to ```
default 2
``` if you want the third item

---

### Post by ad_267 on 2008-04-26
You will need to have superuser privileges to edit this file. So you will need to open up a terminal and type:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
to backup the menu.lst file then:
```
gksu gedit /boot/grub/menu.lst
```

---

