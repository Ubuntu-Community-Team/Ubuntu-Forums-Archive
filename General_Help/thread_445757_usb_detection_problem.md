---
title: "usb detection problem"
date: 2007-05-16
forum: General Help
---

### Post by punkska101 on 2007-05-16
Hi,

i've got problem with my usb rca 1028 lyra player. I've found a way to mount my player to transfer files but i've encounter a strange problem from time to time when i connect my player and sudo fdisk -l my drive will be recognize as a different /dev/sda number for example i'll connect my player 

sudo fdisk -l

/dev/sda1
/dev/sdb1

on next disconnection reconnection i'm

/dev/sda1
/dev/sdc1

i've made my self a little script to mount my mp3 player but the changing of letter creates problem 

> sudo mount /dev/sda1 /media/lyra -w -o uid=1000,gid=1000
sudo mount /dev/sdb1 /media/lyra2 -w -o uid=1000,gid=1000

logs doesn't show much but maybe I don't know what to look for

thx for your help 

Jo

---

### Post by MoLE on 2007-05-23
You might want to explore getting around this by using a UUID= descriptor for your mp3 player in fstab.  This will link your mp3 player with the same mount point regardless of the device used. 

Any wiser heads know if this would work?

---

