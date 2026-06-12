---
title: "GRUB Help"
date: 2007-12-13
forum: General Help
---

### Post by BuddhaDave on 2007-12-13
I am new to unix/linux systems but not to computers and software.
I want to edit the GRUB menu so windows is the first or default system to boot.
I can make the changes but not save them because it thinks I am not the owner?
How do I open the edit with owner permission.

---

### Post by viking777 on 2007-12-13
```
sudo gedit /boot/grub/menu.lst
```

or 

```
sudo kate /boot/grub/menu.lst
```

---

### Post by strabes on 2007-12-13
See these pages for more info:
[http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)
[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

You should take this section:> title		Windows XP LOL!!!!!!!!
root		(hd0,0)
savedefault
makeactive
chainloader	+1

and put it above the section that looks like this:> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0ad151c3-f3d3-4f08-9507-c69b483d8c8d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

---

