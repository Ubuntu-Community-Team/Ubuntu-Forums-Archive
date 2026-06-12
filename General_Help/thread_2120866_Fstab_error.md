---
title: "Fstab error"
date: 2013-02-27
forum: General Help
---

### Post by ubunet on 2013-02-27
Hi guys,

My Xubuntu 12.10 x86 on boot show me a error in fstab like "option 'erros=remount-ro' not recognized.

[http://img10.imageshack.us/img10/4435/dscn27321.jpg](http://img10.imageshack.us/img10/4435/dscn27321.jpg)

Yesterday, everything works fine.

---

### Post by nothingspecial on 2013-02-27
Hi,

> "option 'erros=remount-ro' 

you are missing an r

needs to be errors not erros

Do you have a live cd or usb ?

---

### Post by steeldriver on 2013-02-27
It needs to say

```
erro[COLOR=Red]**r**[/COLOR]s=remount-ro
```Luckily it looks like it has managed to boot as far as the root shell, so you should be able to edit the file to correct it without needing to boot from a live CD / USB - you may need to remount with read-write permissions first though i.e.

```
mount -o remount,rw /
```

then edit the /etc/fstab file

---

### Post by ubunet on 2013-02-27
**Ok, works!** Solved the problem of the fstab, but I still** can't** start Xubuntu. Look:
[http://ubuntuforums.org/showthread.php?t=2120832](http://ubuntuforums.org/showthread.php?t=2120832)

---

