---
title: "Resize the system.virtual.disc"
date: 2007-07-27
forum: General Help
---

### Post by moshazat on 2007-07-27
Hello, i have a problem and question related to resizing the system.virtual.disc. I'm really new about this ubuntu n since i tried this os, i really like it so much and i keep installing software until i run out of space. i choose to have 6GB when i'm installing wubi. Now im trying to increase the size to extra 2GB of my virtual disc and i check out the Wubi Guide and they show the solution. I tried to follow but i have questions n problems ;

The Wubi Guide write ;
> How do I resize system.virtual.disk?
1.Create the file extra.virtual.disk of the desired size (see above) and place it under C:\wubi\disks. 

2.Boot into Ubuntu and run the following code (you can cut and paste it into a terminal): 

[QUOTE]sudo mkfs.ext3 /dev/loop4 
sudo mount /dev/loop4 /media/extra
sudo rsync -avx --exclude '/sys/*' --exclude '/proc/*' / /media/extra

3.Boot into windows and rename extra.virtual.disk to system.virtual.disk. [/QUOTE]

My question is ;
1. How i want to create the extra.virtual.disc? I really have problem with this, can use other than using qemu? i want to try the dirty trick but i dont know how to create 2GB virtual disc. can u recommend some method plz :)
2. After i end this method after run those code and rename the extra to system, then is it all the file and application in the system.virtual.disc will be erase in the new virtual disc size?

Other than that, i want to have multiple linux installations at the same time, i already install ubuntu with wubi, then now i want to make another virtual disc for ubuntustudio, then i tried following the guide. I tried to reinstall but it says it will uninstall the current ubuntu in my computer. Then i can choose windows or ubuntu, and then ubuntu or ubuntustudio at the boot menu:)

I hope somedy help me, i really need guide bcoz i really interested with linux xspecially ubuntu, thank you and sorry for my english

MOSHAZAT

---

### Post by tuxcantfly on 2007-07-28
> Other than that, i want to have multiple linux installations at the same time, i already install ubuntu with wubi, then now i want to make another virtual disc for ubuntustudio, then i tried following the guide. I tried to reinstall but it says it will uninstall the current ubuntu in my computer. Then i can choose windows or ubuntu, and then ubuntu or ubuntustudio at the boot menu

Go to [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) and see the section that says "Ubuntu Studio Repository" that'll let you install ubuntu studio under your existing ubuntu install through apt-get.

> How i want to create the extra.virtual.disc? I really have problem with this, can use other than using qemu? i want to try the dirty trick but i dont know how to create 2GB virtual disc. can u recommend some method plz

[https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d](https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d)

---

### Post by moshazat on 2007-07-28
thank you tux :D

if i increase the storage, is it will effect or erase all my system.virtual.disc if i want to resize the system?

---

### Post by tuxcantfly on 2007-07-29
> i have one question, if i do the method to resize the system.virtual.disc, then all my file in the system.virtual.disc will be erased/format after i resize? or it will remain there?

They'll remain there
> 
then if i want to resize the size, so in the command i should put the size i want to add or the actual size i want it to be?

for example, currently i have 5GB, I want to make it 8GB, then in the command to make virtual disc i shoulD put 3GB OR 8GB?

8GB

---

