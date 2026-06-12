---
title: "Error 1"
date: 2008-05-30
forum: General Help
---

### Post by vestige00 on 2008-05-30
I install Ubuntu 8.04 LTS, and I'm duel-booting with XP Home.  I get to the screen to choose between the two and this error comes up: "Error 1: Filename must be either an absolute pathname or block list"  Some1 help me plz :confused:

---

### Post by Shazaam on 2008-05-30
Did you manually edit grub? From herman's grub page---
"Quoted from the GNU/GRUB manual
1: Filename must be either an absolute filename or blocklist.
This error is returned if a file name is requested which doesn't fit the syntax/rules listed in the Filesystem. 
One way to produce this error on purpose at GRUB's Command Line Interface is to type something like 'kernel (hd0,1) vmlinuz'
The correct way to type it is with the forward slash to indicate the root of the file system, like this, 'kernel (hd0,1)/vmlinuz'
Check to make sure your menu.lst doesn't have a syntax error like that."

From here...
[http://users.bigpond.net.au/hermanzone/p15.htm#1](http://users.bigpond.net.au/hermanzone/p15.htm#1)

---

### Post by vestige00 on 2008-06-01
how do u manually edit grub?  where is the directory located?  i see edit in the black screen, by hitting "e", but im not sure if that's how i fix it:confused:

---

### Post by meierfra. on 2008-06-01
Does "error 1" pop up when you choose "ubuntu"? "windows"? both? or even before you choose an OS?

Boot from the Ubuntu LiveCD, double click the icon for the Ubuntu partition (it is either on the desktop, or go to "Places->Computer") Browse to /boot and than to /boot/grub. Open  the file "menu.lst" and post its contents here.

Also open a terminal (Applications->Accessories->Terminal) and post the output of 

```
sudo fdisk -l
```

(l is a lowercase L)

To open menu.lst for editing you need to use:

```
gksudo gedit /media/disk/boot/grub/menu.lst
```


(Here you have to replace "disk" by whatever it says underneath the Ubuntu icon)

---

