---
title: "no sata disk on ubuntu"
date: 2008-04-04
forum: General Help
---

### Post by borgixx on 2008-04-04
hello i installed ubuntu on my intel celeron, and now i can-t see my sata disk. Can anyone please help on how to recognize it. BTW its a grub dual with windows XP and in xp it-s recognized normally... :confused:

---

### Post by tamoneya on 2008-04-04
What have you tried?  Have you attempted to mount ```
sudo mount /dev/sda1 /some_directory
```
What is the Filesystem on the sata? FAT32? NTFS? ext3?

---

### Post by borgixx on 2008-04-04
no theres nothing there as something to be as my sata disk when i type mount  so i guessed that there is nothing to mount

---

### Post by sisco311 on 2008-04-04
open a terminal:

Applications -> Accessories -> Terminal

and post the output of this commands:

```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
```

---

### Post by tamoneya on 2008-04-04
```
sudo apt-get install gparted
sudo gparted
```
that will start a partition manager and you can look to see what is available.  What type of filessytem is it?

---

### Post by borgixx on 2008-04-04
i already installed gparted and i can see it in gparted. I don't know if the problem is that i first installed ubuntu without SATA and then i plugged it in. ? :confused:

---

### Post by tamoneya on 2008-04-04
what is the device name in gparted? what is the filesystem?

---

### Post by borgixx on 2008-04-04
sorry i have to go so wont be able to respond, in gparted it shows like /dev/sda1 (but when i type mount its not there). Culd it be possible to try to solve this after, when i return please ? PS filesystem is NTFS

---

### Post by tamoneya on 2008-04-04
try specifying the filesystem explicitly.  also put it in verbose mode
```
sudo mount -V -t ntfs /dev/sda1 /some_directory
```

---

