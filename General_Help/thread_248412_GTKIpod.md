---
title: "GTKIpod"
date: 2006-09-01
forum: General Help
---

### Post by wizzkid on 2006-09-01
Hi Guys

I have IPOD Video 30GB. and I installed GTKIPOD to be able to upload mp3 to my Ipod. 

After installing GTKIPOD, I run it and click on "READ" icon, however, I encounter error message:
'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.

Also, can you guys, tell me how to upload music to my ipod using GTKIPOD? if there are good software that manages IPOD, I am glad to hear it. 

Thanks a lot.

---

### Post by aysiu on 2006-09-01
I don't have an iPod, but I've heard AmaroK and Banshee work well with iPods.

---

### Post by 3rdalbum on 2006-09-01
Has your iPod already been formatted using the Windows program that comes with it?

Also, does your iPod appear on the desktop when you plug it in?

---

### Post by wizzkid on 2006-09-01
Hi, I havent formatted my ipod.. its out from the box. I used iTunes windows to transfer files. When I plugged the USB, my ipod appears on the desktop. 

Hope you could help! 

Thanks!

---

### Post by wizzkid on 2006-09-07
Any help from here? :) hopefully, you guys could help me here. 

Thanks.

---

### Post by L0N3W0LF on 2008-06-03
I know this thread is 2 years old but for anyone who sees this: GTKipod can't make the directories needed because it doesn't have permission to write the files (or so I think) so you have to make them manually (exp: sudo mkdir /media/ipod/iTunesDB.. etc). Since yours was out of the box you should have loaded it on iTunes first so it can make all the necessary directories. And did you check if your iPod was mounted on /media/ipod/? You can remount it. Use umount (exp: sudo umount /dev/sdc1/) to unmount your iPod and then mount it again (exp: sudo mount /dev/sdc1/ /media/ipod/). Use sudo fdisk -l to check out wich device your iPod is (it was /dev/sdc1/ for me). It worked for me (using hardy heron). Hope anyone sees this xD.

EDIT: Typo

---

