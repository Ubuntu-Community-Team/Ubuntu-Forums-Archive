---
title: "partition resiste ext3"
date: 2007-05-26
forum: General Help
---

### Post by palemmo on 2007-05-26
Hello, 
this is my hd current situation:
[img]http://i127.photobucket.com/albums/p124/palemmo/guida/gparted1.png[/img]
I want to resize the hda1 ext3 containing kubuntu(home and root togheter), in order to use all the unallocated space. But to act on ext3 I have to umount it, so I must use a live linux...but also with live kubu the situation does't change.... How can I?
Selecting the ext3 as you can see all the buttons are disabled:
[IMG]http://i127.photobucket.com/albums/p124/palemmo/guida/gparted2.png[/IMG]
It's obviuos that even if the images are made with gparted on the live kubu I'll use qparted, that is not important because for what I have to do the commands are the same...

PS supposing is mounted sda1....where should be? And to umount it can I digit something differente from: 
mount /dev/sda1 /home/user/Desktop/temp
umount temp

something similar to an id code of sda1....so i can "umount idcode"
thanks
Alessio

---

### Post by smoker on 2007-05-26
hi, i tend to have problems with the unbunu live cd gparted, now i only use the 'gparted live cd' and have never had any problems. if you want to download and try it:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

best of luck

---

