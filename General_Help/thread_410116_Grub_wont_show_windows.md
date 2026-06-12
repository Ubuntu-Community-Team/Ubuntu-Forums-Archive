---
title: "Grub wont show windows"
date: 2007-04-15
forum: General Help
---

### Post by jsw4773 on 2007-04-15
Hi
My first cry for help. using dapper and vista. I have installed and wiped ubuntu before without any problems and now reinstalled.  When Grub launches it does not display Windows Vista in the list, just two entries for each of the 2 kernels and memtest. I can mount both windows partitions from ubuntu but i am unable to boot into vista. Can anyone help please.

---

### Post by Adramelech on 2007-04-15
i think you need to update menu.lst manually.

First backup your menu.lst so you dont regret later =).

sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst-backup

then edit it:

sudo nano /boot/grub/menu.lst

and the end of the file add:

title           Microsoft Windows VIsta           
root                 (hd1,0)
savedefault
makeactive
chainloader     +1

(hda1,0) is the partiton where you have your vista installation, if you have ubuntu and vista on diferent hard disc you might have some trouble, if you do, post it and I will help you.

---

### Post by confused57 on 2007-04-15
> **jsw4773 said:**
> Hi
My first cry for help. using dapper and vista. I have installed and wiped ubuntu before without any problems and now reinstalled.  When Grub launches it does not display Windows Vista in the list, just two entries for each of the 2 kernels and memtest. I can mount both windows partitions from ubuntu but i am unable to boot into vista. Can anyone help please.
Post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

If your Vista is on the 1st partition, the Window's example in your menu.lst may boot your Vista...see the 3rd link in my signature for how to edit your /boot/grub/menu.lst...you may prefer to just add your Vista entry at the very end of the file.

---

### Post by jsw4773 on 2007-04-15
Thanks - Got it working by manually editing updating menu.lst. Had to change 'root(hd1,0)' to root (hd0,1). Vista now takes an age to boot and seems to run slower although that could be my imagination but at least i can get into it now.

---

