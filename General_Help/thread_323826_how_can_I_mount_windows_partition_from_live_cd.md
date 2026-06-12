---
title: "how can I mount windows partition from live cd?"
date: 2006-12-22
forum: General Help
---

### Post by bionnaki on 2006-12-22
a friend's windows crashed and he needs a few important documents to be saved. how can I mount the windows partition using the ubuntu live cd?

thanks!

---

### Post by Greevous on 2006-12-22
Bionnaki, 


Enter these in a terminal, separately.
```

$ mkdir /mnt/current 
$ mount /dev/hdXY /mnt/current
```
(X and Y refer to drive and partition that you have Windows installed on.)

The drive is usually hda1 through hda5, depending on how many drives and partitions you have in your computer.

---

### Post by Markalus on 2007-12-13
I have the same issue but when I try to put the commands in terminal I get a permission denied error.
Any idea how to work around that? Thanks.
-M-

---

### Post by fjgaude on 2007-12-13
You need to use sudo before each of the commands;

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows
```

---

### Post by strabes on 2007-12-13
Isn't the 2nd command going to be:```
sudo mount /dev/sda1 /media/windows
```

Since feisty everything is labeled with "s"

---

### Post by vanadium on 2007-12-13
Check your drive names first using the command

sudo fdisk -l

or easier:

blkid

---

### Post by Lostincyberspace on 2007-12-13
> **strabes said:**
> Isn't the 2nd command going to be:```
sudo mount /dev/sda1 /media/windows
```Since feisty everything is labeled with "s"

It is only labeled with an s  if it sata, hd denotes Ide.

---

