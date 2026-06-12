---
title: "Grub displays Ubunto twice"
date: 2006-09-19
forum: General Help
---

### Post by Demio on 2006-09-19
Hello.

I just booted my system and I noticed 2 Ubuntu choices in GRUB (actually 4)

Ubuntu
Ubuntu (recovery)
Ubuntu
Ubuntu (recovery)

How do I delete the cloned entries?

Thanks in advance,
Demio

---

### Post by Anduu on 2006-09-19
If you look closely you should notice the kernel versions are different.

This is done on purpose in case a kernel update breaks something you still have a fallback.

---

### Post by wdbreen on 2006-09-20
Demio,
If you dont strike trouble with the latest kernel (hopefully its 2.6.15-27) then you can delete the older version using:
sudo apt-get remove linux-image-2.6.15-.............then
sudo update-grub

I would advise that you keep at least two images loaded at any one time, purely for emergency backup.

You can pre-select a kernel to load at startup by editing /boot/grub/menu.lst

---

### Post by Demio on 2006-09-20
Oh, I guess that makes sense hehe. I didn't pay attention to that detail at first.

Thanks,
Demio

---

### Post by dasuberdog on 2006-09-20
How do you make a kernal your default kernal?  I have the k7 version and with updates I get the 386 version and acidentally downloaded it.  So how do I make the k7 one the default one again?

---

### Post by Fully216 on 2006-09-20
You need to edit your /boot/grub/menu.lst so that a default is assigned to the version of your choice instead of the newest version available.  Change `default saved' to the number of the desired version.

For general information, check out [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

This also give specifics on what you need here [http://www.gnu.org/software/grub/manual/grub.html#Booting-once_002donly](http://www.gnu.org/software/grub/manual/grub.html#Booting-once_002donly)

---

