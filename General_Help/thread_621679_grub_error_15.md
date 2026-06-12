---
title: "grub error 15"
date: 2007-11-23
forum: General Help
---

### Post by notatoad on 2007-11-23
i installed ubuntu again today, and when i rebooted i got grub error 15.  my partition is set up so that sdc is recognized as hd3 in grub.  / is on partition (hd3,0),  /home is (hd3,1), and var is (hd3,5).

i am following this: [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)

i have mounted my install in /ubuntu and chrooted into it.  my devices.map is accurate, and i am in the grub prompt.  i attempt to do "root (hd3,0)" and i get error 21 - selected disk does not exist.  what is happening?

menu.lst points to hd3,0 as it should, and the file it points to exists.

---

### Post by torgrot on 2007-11-24
post the output of 
sudo fdisk -l  that is a lower case l

torgrot

---

### Post by meierfra on 2007-11-24
You might already know, but  mwardle's post has a misprint.  Instead of "grub --device.map=device.map" you need to run
```
grub --device-map=device.map
```


In addition  to fdisk,  also post your device.map. and the output of 

```

grub --device-map=device.map
find /boot/grub/menu.lst

```

(You need to chroot and  cd to /boot/grub before you issue the last two commands)

Does the grub menu appear at boot-up?

---

### Post by notatoad on 2007-11-24
device.map:
```
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc

```

the last (the important) bit of fdisk:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1401    11253501   83  Linux
/dev/sdc2            1402        2694    10386022+  83  Linux
/dev/sdc3           14094       14593     4016250   82  Linux swap / Solaris
/dev/sdc4            2695       14093    91562467+   5  Extended
/dev/sdc5            2695       14093    91562436   83  Linux

```

find menu.list gives error 15:file not found.

---

### Post by notatoad on 2007-11-24
i've just reinstalled again and i'm getting the exact same problem

---

### Post by meierfra on 2007-11-24
> find menu.list gives error 15:file not found.


Very strange. Did you do  "find /boot/grub/menu.lst" or just "find menu.lst"

Does the grub menu appear at boot-up?

---

### Post by notatoad on 2007-11-24
no, i did find /boot/grub/menu.lst  and i tried a couple of times.  it definitely wasn't a typo or something, and the menu.lst file definitely exists.  

on boot i get the error15 code before any grub menu shows up.

---

### Post by meierfra on 2007-11-24
I think I know what the problem is:

try to chroot ubuntu as follows:

sudo mkdir /ubuntu   
sudo mount -t ext3  /dev/sdc1 /ubuntu
sudo mount -t proc none /ubuntu/proc
sudo mount -o bind /dev /ubuntu/dev
sudo chroot /ubuntu

---

### Post by notatoad on 2007-11-25
well, that let me do root and setup in grub, but i still get error15 on boot.  i think i'm going to try to install on an IDE hard disk, see how that works.

---

### Post by meierfra on 2007-11-25
Is hda    sda sdb  sdc the boot sequence in the bios?  Do you have a raid?

---

