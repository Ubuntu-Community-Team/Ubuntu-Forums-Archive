---
title: "Prepair partition"
date: 2008-05-23
forum: General Help
---

### Post by raedbenz on 2008-05-23
Hi..
I want to install Ubuntu, but i need to keep windows. 
If I create a partition in Windows, then go to Ubuntu installation and use it for Linux.
Will it work ? or it should had been created from Linux?
thanx

---

### Post by NightwishFan on 2008-05-23
I would use the partition editor on the live cd, however Ubuntu should be able to make use of any prepartitioned free space. Use what you are familiar with.

---

### Post by raedbenz on 2008-05-23
> **NightwishFan said:**
> I would use the partition editor on the live cd, however Ubuntu should be able to make use of any prepartitioned free space. Use what you are familiar with.

Thanks..
Onemore things. lets say i have in windows C and D drives.
Then i create E (also from windows, size 20Gb). Then in Ubuntu's partition editor i ll see the 20 Gb drive and i use as "/" mount point. 
Q1. but From where do i get the space for SWAP drive?
Q2. Does this mean i need to crate to drives before i start installation (as in my case from windows)??

thanx

---

### Post by HunterThomson on 2008-05-23
> **raedbenz said:**
> Thanks..
Onemore things. lets say i have in windows C and D drives.
Then i create E (also from windows, size 20Gb). Then in Ubuntu's partition editor i ll see the 20 Gb drive and i use as "/" mount point. 
Q1. but From where do i get the space for SWAP drive?
Q2. Does this mean i need to crate to drives before i start installation (as in my case from windows)??

thanx

Ya, I am fairly sure that you need to create a swap partition roughly twice the size of your RAM or at lest 256MB. If you really make a /  "root" partition on that new partition. NOW, if you create a new partition and it is seen as free space then in the Ubuntu installer you choose the option to install to the longest contuis free space then it will put all on that free space including a swap partition.

---

### Post by raedbenz on 2008-05-23
HI HunterThomson,

u mean that from -lets say- windows i have to create  to drives ?
one large for "root" and one small(around 1Gb) for Swap?
Yes or no?
thanks

---

### Post by HunterThomson on 2008-05-23
Your best beet, if you ask me, is to use the partitioner on the Live Ubuntu CD and just shrink the D partition down 20GB and do not create a new partition there. Just shrink the D partition and leave it as free space then restart. Then install and in the installer when you get to the partitioning section you should see a option to install to that free space and leave the rest of the harddrive alone. Then you will have a all of Ubuntu including a swap partition on that free space as well as a swap.

---

### Post by raedbenz on 2008-05-23
Thanx....
But if i shrink D to 20Gb, will i loose the data already in that drive?
because i use it as a storage for my personal documents in Windows.

thanks again

---

### Post by HunterThomson on 2008-05-23
> **raedbenz said:**
> HI HunterThomson,

u mean that from -lets say- windows i have to create  to drives ?
one large for "root" and one small(around 1Gb) for Swap?
Yes or no?
thanks

Yes. 

However, that is just a hard way to do it. If you want to patition your harddirve. I would shrink the D partion in the Ubuntu live cd patitioner to 
create free space. Then in the installer you will get to a section for partitioning. There you can chose the Manual partitioning option. In there you can create new partitions. I would create them like this...

all logical partitions.

150MB ext2, labelled /boot
1GB SWAP
10GB ext3, labelled /
5GB ext3, labelled /home This is normaly the rest of the free space on the harddrive. However, this is where your Music and vids will be kept but if you just keep them on the D partition you will not need this partition to be all that large. In this case you will just want it so if you reinstall all your setting will not be lost.

---

### Post by HunterThomson on 2008-05-23
> **raedbenz said:**
> Thanx....
But if i shrink D to 20Gb, will i loose the data already in that drive?
because i use it as a storage for my personal documents in Windows.

thanks again

I just meen you need to free up like 20GB of space on your harddrive for Ubuntu. I think 8GB min???

---

### Post by raedbenz on 2008-05-23
> **HunterThomson said:**
> I just meen you need to free up like 20GB of space on your harddrive for Ubuntu. I think 8GB min???

Thats true, i ll use 8Gb for Ubuntu and the rest as home directory...
thanx

---

### Post by HunterThomson on 2008-05-23
> **raedbenz said:**
> Thats true, i ll use 8Gb for Ubuntu and the rest as home directory...
thanx

The one thing with that is that the default temp directory for everything is in /temp which will be in the / "root" directory. So, if you want to convert a avi to mpeg you will need like 1GB or like 4.7Gb of free space in the / partition in order to do the covertion. However you could just go to the Avidemux.config and change it....

---

### Post by raedbenz on 2008-05-23
> **HunterThomson said:**
> The one thing with that is that the default temp directory for everything is in /temp which will be in the / "root" directory. So, if you want to convert a avi to mpeg you will need like 1GB or like 4.7Gb of free space in the / partition in order to do the covertion. However you could just go to the Avidemux.config and change it....

Hi,,,
i installed Ubuntu succesfully...
the thing is i did a mistake and the whole size of the drive i used it as a "root".
so now if i need to install or save files , can i use the root directory ?
or i have to create a "home" directory???
thanks

---

### Post by forestpixie on 2008-05-23
You will have a /home in the root directory which the system will use.

Good luck with it.

---

