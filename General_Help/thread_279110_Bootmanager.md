---
title: "Bootmanager"
date: 2006-10-17
forum: General Help
---

### Post by korpral on 2006-10-17
How do I remove all of the choices for OS in the boot manager, I only want win and ubuntu... But now i have like 4 chocies for ubuntu and another one for " other os" .. And i only have win and ubuntu.
Plz help me

---

### Post by bulldog on 2006-10-17
Keep cool it isn't that important.

Just set a # for each line of a kernel you don't want to see in your GRUB

Open your menu.lst after making a backup.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
Then alter it,```
gksudo gedit /boot/grub/menu.lst
```

```
#title		Ubuntu, kernel 2.6.15-27-k7
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro quiet splash #vga=792
#initrd		/boot/initrd.img-2.6.15-27-k7
#savedefault
#boot
```Like this.

Save the file and your done.

---

### Post by nikhilk on 2006-10-17
To make things easier post the contents of your "/boot/grub/menu.lst" file

---

