---
title: "Creating a Swap File"
date: 2004-10-28
forum: General Help
---

### Post by Conquerer on 2004-10-28
Is there any way to create a swap partition after installing Ubuntu? I can create another partition, but how do I assign it. Help please.


-Conquerer

---

### Post by ubuntu-geek on 2004-10-28
[QUOTE=Conquerer]Is there any way to create a swap partition after installing Ubuntu? I can create another partition, but how do I assign it. Help please.


-Conquerer[/QUOTE]
 Going off memory..

fdisk /dev/hdx
enter "t" (without qoutes)
select the newly created partition
select the type "swap"
then enter "w" to write the changes

mkswap /dev/hdx
swapon /dev/hdx

I think that should do what ya need :)

---

### Post by jdong on 2004-10-28
That'll activate it for one session. You need to edit **/etc/fstab** with the following line:

**/dev/hda3       none            swap    sw              0       0**

---

### Post by ubuntu-geek on 2004-10-28
[QUOTE=jdong]That'll activate it for one session. You need to edit **/etc/fstab** with the following line:

**/dev/hda3       none            swap    sw              0       0**[/QUOTE]
 :) oh yeah forgot about that..

---

