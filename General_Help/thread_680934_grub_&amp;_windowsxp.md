---
title: "grub &amp; windowsxp"
date: 2008-01-28
forum: General Help
---

### Post by jtmedin on 2008-01-28
Using grub to dual boot, had to reinstall windowsxp & now grub sees 2 windows. One of the windows is inop. How do i get only the correct windows to show?. BTW have 2 hd, one is windows & the other is ubuntu.

---

### Post by gvartser on 2008-01-28
[COLOR="Red"]**Note!**
**If made wrong you can risk not being able to start your OS:es**.[/COLOR]

You can edit /boot/grub/menu.lst, but remember to take a backup of the "menu.lst" file before editing..

1) move into /boot/grub
```
cd /boot/grub
```

2) Make a backup of your /boot/grub file
```
sudo cp menu.ls menu.ls.backup
```

3) Use your fav editor to edit the file "menu.lst": (NOTE! You have to be root to edit the file, use "sudo")
   At the bottom of the file you will see all the options that are presented to you while booting your machine.
   Uncomment the block that you want to remove from the GRUB list.

```
Example: (Note your will have something with Windows in it. 
#title           Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.22-14-server #root=UUID=9e1ff002-cbd8-4213-a8f8-a3ecba91a32b ro single
#initrd          /boot/initrd.img-2.6.22-14-server
```

4) Save the file and the reboot.

---

### Post by jtmedin on 2008-01-31
Sorry thats not the problem. Grub lists the windows loader but when i select that i get 2 windows xp & windows xp#1. Think that is on the windows hd & probably duplicate because i had to reinstall windows. Any other ideas? TIA

---

### Post by polmir on 2008-01-31
type in terminal

```
sudo fdisk -l /dev/sda
sudo fdisk -l /dev/sdb
```
sda or hda
sdb or hdb
```
gedit /boot/grub/menu.lst
```

please post out of it

---

### Post by logos34 on 2008-01-31
In that case you need to remove it from your windows **boot.ini** file.

---

### Post by jtmedin on 2008-02-08
Ok that solves it. Thanks

---

