---
title: "Logging into blank home folder instead of my home folder"
date: 2012-10-26
forum: General Help
---

### Post by akshay4876 on 2012-10-26
So I kind of utterly fubared my boot loader. I used boot repair to fix  it. 
Then when i logged into my Ubuntu i get a blank home folder. Now  when i check to see how much space is left. I realize that my old home  folder is still in memory. 
Anyway to get it out? Also i was messing with my home folder with livecd because it is  randomly encrypted and I do not know the passphrase. What I altered  where the permission in the folder using a root nautilus.
 So help would be good since I just want to get my data back and reformat  the hard drive and do a fresh install.
Ubuntu: 12.04LTS 
Thanks
By the way: I really need the data to finish my work

---

### Post by dino99 on 2012-10-26
check your real partition uuid:

sudo blkid

then compare with fstab ones

sudo gedit /etc/fstab

if there is a difference, then use the one given by blkid

---

### Post by akshay4876 on 2012-10-26
Nevermind I saw what the problem was. I had to dencrypt my data from the .private folder--something that i never had to do before. I looked up how to do it and was good to go. Thanks anyway.:guitar:

---

