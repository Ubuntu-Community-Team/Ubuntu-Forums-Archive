---
title: "If I upgrade to 13.04, how hard or easy would it be to go back to 12.04LTS"
date: 2013-05-01
forum: General Help
---

### Post by alhefner on 2013-05-01
I've used the backup utility in Ubuntu to back up my 12.04LTS files. I'm thinking about giving 13.04 a shot but want to make sure I can simply restore and get the 12.04LTS back if things don't work out right.

---

### Post by claracc on 2013-05-01
You will have to do a fresh install of ubuntu 12.04 and then restore your backed up home files.

There is not any other go backwards when you upgrade to 13.04.

---

### Post by Bucky Ball on 2013-05-01
*Thread moved to **General Help**.*

> **claracc said:**
> You will have to do a fresh install of ubuntu 12.04 and then restore your backed up home files.

There is not any other go backwards when you upgrade to 13.04.

Correct. There is no downgrade option. I suggest, if you have the space, you install 13.04 to another partition. Then, if it breaks, you have the stable 12.04 LTS to fall back on. You can use the same /home partition, if you have one, and /swap that 12.04 LTS is currently using and you will be able to access files in the directory /home in 12.04 if you don't have a /home partition. Having different releases on separate partitions is pretty normal for testing releases. I generally run the LTS as my main squeeze and have a couple of spare partitions for playthings, the interim releases or anything else I fancy. You could also try running 13.04 as a virtual machine using Virtualbox ... 

Out of curiousity, are you just curious to try 13.04 or is there something specific?

---

### Post by Mark Phelps on 2013-05-01
Another option, which I have used, is to image off your current install using Clonezilla, to an external drive, or to another partition.

That way, if the upgrade goes badly, it only takes a few minutes to restore the older, working version, of Ubuntu.

---

### Post by sudodus on 2013-05-01
> **Mark Phelps said:**
> Another option, which I have used, is to image off your current install using Clonezilla, to an external drive, or to another partition.

That way, if the upgrade goes badly, it only takes a few minutes to restore the older, working version, of Ubuntu.

+1
The safest option is to make an image onto an external drive and disconnect it. Then a failing installation has no chance to mess with the backup image.

---

### Post by Buntu Bunny on 2013-05-01
> **Mark Phelps said:**
> Another option, which I have used, is to image off your current install using Clonezilla ....

I didn't know about Clonezilla but it sounds excellent, thanks!

---

### Post by pfeiffep on 2013-05-01
> **alhefner said:**
> I've used the backup utility in Ubuntu to back up my 12.04LTS files. I'm thinking about giving 13.04 a shot but want to make sure I can simply restore and get the 12.04LTS back if things don't work out right.
It won't be quite as responsive as your 12.04 hard drive installation but you could make a bootable flash drive to evaluate 13.04. Once I installed 13.04 I found it faster than 12.10!

---

### Post by alhefner on 2013-05-01
> **Bucky Ball said:**
> *Thread moved to **General Help**.*



Correct. There is no downgrade option. I suggest, if you have the space, you install 13.04 to another partition. Then, if it breaks, you have the stable 12.04 LTS to fall back on. You can use the same /home partition, if you have one, and /swap that 12.04 LTS is currently using and you will be able to access files in the directory /home in 12.04 if you don't have a /home partition. Having different releases on separate partitions is pretty normal for testing releases. I generally run the LTS as my main squeeze and have a couple of spare partitions for playthings, the interim releases or anything else I fancy. You could also try running 13.04 as a virtual machine using Virtualbox ... 

Out of curiousity, are you just curious to try 13.04 or is there something specific?

Thanks for all the help everyone. 

Bucky Ball, I've seen posts about 13.04 and it seems that they have included some things that 12.04LTS didn't have that I needed such as the drivers for my wired Ethernet. Also, I've been having problems with the GPU hanging in 12.04 (it's a bug being worked on) while using Firefox and at other random times. Just curious if that had been fixed in the newer version.

---

### Post by Bucky Ball on 2013-05-01
Personally, I'd install it on a spare partition and give it a whirl as trying it by booting from the disk won't be the same experience; you may be limited in what drivers you can install so you won't find out if those problems are fixed anyhow. Good luck.

---

