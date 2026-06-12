---
title: "Writing on a partition after partitionning it under Windows"
date: 2007-10-19
forum: General Help
---

### Post by Concept on 2007-10-19
Dear All, 

I ve made the big plundge, Ubuntu is part of my machine...while things get usually quite straighforward and follows a "reasonable process" to be installed, I start appreciating it. looks like Linux is no longer a Myth of microsoft rebels lool...( I am joking I know that linux developpers are worth more than this title of course)...

Well, the reason of this post is ?

After installing ubuntu, I realized that I forgot to format a remaining partition. Having a Dual boot, I ve used a windows software to format the remaining part (acronis partion expert), and I ve made sure that ntfs-3g is properly installed from the Ubuntu side. 

Logging as "myusername" I am not able to write on this newly created partition....when I go to properties, it is written that the partion owner is "root"

So my feeling is that I must open a terminal, write "sudo su-" to be able to do whatever I want..

but I dont know how to specify that such partition is supposed to be writable by any user or at least one (myusername)

I would like also to rename this new partition together with  the existing one...to give them a name more consistent with theiir content.

Your feedback will have my consideration, thanks.


T.

---

### Post by Concept on 2007-10-20
ok Guys, it was a piece of cake almost ridiculously easy.

[ 0) Context: After installing Ubuntu 7.04, you d like to install another Hard disk already formatted in ntfs. You ve made sure that nfts-3g was already installed. We assume in addition that, the hardisk is physically connect to the motherboard.]


1)  you check if the disk is physcically recongnized by: 

*sudo fdisk -l | grep NTFS*

you discover one more line than usual, in my case:

/dev/sdb5            5100       38913   271610923+   7  HPFS/NTFS

2)  you create a directory in "/media" where you wish to mount this harddisk, in my case I simply called this directory "sdb5"

3)  then you mount the harddisk using ntfs-3g according to:

*sudo ntfs-3g  /dev/sdb5 /media/sdb5*

4) you dont forget to edit the file fstab 

*gksu gedit /etc/fstab*

you add one more line that matches in argument with the preexisting line but applied to the new hardisk. You shall find the "UUID" in System-> preference->Hadrware information.

This was my first (humble) contribution to the community...


T.

---

