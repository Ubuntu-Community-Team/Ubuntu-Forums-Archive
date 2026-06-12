---
title: "ubuntu on master xp on slave"
date: 2007-06-08
forum: General Help
---

### Post by bzburr on 2007-06-08
Hello, 

first off - isn't ubuntu brilliant!

Now for my question:

I have Ubuntu (7.04) installed on my Master Drive and XP on my slave.
I didnt have the balls to install ubuntu while XP slave was connected.

I'd like to have XP listed on the menu which loads during the boot process

Can someone tell me the process for figuring out which hd1,hd0 etc i need to know so i can correctly edit menu.lst so I can dual  boot XP and Ubuntu from the menu?


What information do i need to give you to help?

cheers
Buzz

---

### Post by Rui Pais on 2007-06-08
hi,
do:
```
gksudo gedit /boot/grub/menu.lst
```

and add this (copy+paste to avoid errors) to the end of the file:
> title		Microsoft Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

that should do it.

---

### Post by bzburr on 2007-06-08
hi,
i get "selected disk does not exist" when  select the XP option
:(

Buzz

---

### Post by Rui Pais on 2007-06-08
> **bzburr said:**
> hi,
i get "selected disk does not exist" when  select the XP option
:(

Buzz

well... i suggested root (hd1,0) cause you mention a second slave disc, maybe is not correct. 
Are you sure is connected, working alright and set as slave? 
When you boot to Ubuntu what is the output of:
```
sudo fdisk -l
```

---

### Post by bunker on 2007-06-08
XP doesn't like being on a secondary disk so you might also need to add:

```

map (hd0)(hd1)
map (hd1)(hd0)

```

---

### Post by Rui Pais on 2007-06-08
> **bunker said:**
> XP doesn't like being on a secondary disk 

picky creature (a bet it came out of an X file episode :()

> so you might also need to add:

```

map (hd0)(hd1)
map (hd1)(hd0)

```

yes i remember now i have seen this been recommend several times in the past, sorry i forgot it completely.
(/me take mental note, don't forget that there are OSs that have preferences on the place they occupy on disc...)

---

### Post by bzburr on 2007-06-08
sudo fdisk -l gives the following:


Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        9985    80196480    f  W95 Ext'd (LBA)
/dev/hda2   *       19124       38913   158963175    7  HPFS/NTFS
/dev/hda3            9986       19123    73400985   83  Linux
/dev/hda5               2        9607    77160163+   7  HPFS/NTFS
/dev/hda6            9608        9985     3036253+  82  Linux swap / Solaris

Partition table entries are not in disk order


Buzz

P.S. i was remiss earlier for not thanking your for your time and effort - i do appreciate it, its one of the cool things about the ubuntu community that people offerr to help like this

---

### Post by Rui Pais on 2007-06-08
No problem :) 

do what bunker suggested (post #5).

You have WinXP on /dev/hda2 maybe you need to change root (hd1,0) to root (hd1,1) 
Not sure, maybe bunker can help more on this, or just try both.

(Linux community support is one of the best things Linux have, yes :D)

---

### Post by Rui Pais on 2007-06-08
Oops,

fdisk only list one drive. 
Is this the one that have Linux, the master? You must connect both.

---

### Post by bzburr on 2007-06-08
ahh thanks for tha
for some reason the two hard drives dont play together and i can get bios to only recognise one or the other (or none) never both at the same time

this does not bode well - darn and it was a brand new 320 gig drive too

Buzz

---

### Post by Rui Pais on 2007-06-08
> **bzburr said:**
> ahh thanks for tha
for some reason the two hard drives dont play together and i can get bios to only recognise one or the other (or none) never both at the same time

this does not bode well - darn and it was a brand new 320 gig drive too

Buzz

thats strange, what kind of drives do you have? a new 320 should be SATA but your kernel seems to detect a PATA... And the old one is a SATA or PATA?

---

