---
title: "[SOLVED] Install Ubuntu &amp;quot;inside&amp;quot; Windows using Wubi"
date: 2008-06-10
forum: General Help
---

### Post by Dani Filth on 2008-06-10
My friend is trying out Ubuntu, and since 8.04 has an option which allows use to install and use Ubuntu safely (I think) "inside" Windows, he gave it a try.

However, it seemed like some errors occured. He said that he did install it, he also lost 10GB disk capacity which he gave to Ubuntu. He can "see" it when he view the disk partition in Windows. But, he cannot boot into Ubuntu.

I've never tried Ubuntu "inside" Windows before, what I did was partitioning the disk first, then installed or I chose to installed to the entire hard disk. So I don't know how to deal with this matter.

Does it have to boot to Windows first then log in Ubuntu, or after this installation, Ubuntu will be installed and ready to dual boot together with Windows?

Thanks in advance :D

---

### Post by Dani Filth on 2008-06-10
In addition, he installed Ubuntu in Windows successfully. The first time booting, there's a dual menu with "Windows" & "Ubuntu", and it installed GRUB & stuffs. But after this, he couldn't boot in any of the options "Ubuntu 8.04 kernel..." , "Ubuntu 8.04, memtest86+...", all returned the error :
> root : (hd1,5)/ubuntu/disks
Error 22 : No such partition.
Press any key to continue...
And when he logged into his Windows partition, he could see Ubuntu acting as a 10-GB-folder on the disk.

Thanks!

---

### Post by bumanie on 2008-06-10
The install seems to have gone wrong. Wubi actually uses 15gb of disk space, not 10gb. I would suggest your friend goes to add and remove in windows and remove ubuntu (assuming it has recorded there as it should). > Does it have to boot to Windows first then log in Ubuntu, or after this installation, Ubuntu will be installed and ready to dual boot together with Windows?
 Basically wubi sets up a screen similar to the grub screen giving the choice of booting to windows or ubuntu. I hope it has recorded in add and remove so your friend can try again. I installed ubuntu via wubi on someones vista machine, it works fine, but the issue here is that it seems the install has not gone well. If ubuntu is not recorded in add and remove, post back with questions, someone may be able to help.

---

### Post by Dani Filth on 2008-06-10
Yes, he could easily remove that Ubuntu "folder" in the disk and get back his 10GB. He told me that he has been installing/removing about 2-3 times and he also tried to give Ubuntu 15GB but the fault still occurs.
P.S : He uses Windows Server 2003 as the primary boot, is there any conflict between Windows Server and Ubuntu?
The CD is the CD he ordered from ShipIt, so I think it shouldn't be any problem during burning/recording the image to the CD

---

### Post by wannadumpwindows on 2008-06-10
Maybe you should have him register for the forums. It might help him out a lot. There's all kinds of things to be learned here. :)

---

### Post by bumanie on 2008-06-10
It is possible that there is some type of hardware conflict or something, it happens occasionally to people trying to install from a live cd. They usually have success with the alternate cd, but I'm not sure whether that has the wubi installer.

---

### Post by Dani Filth on 2008-06-10
The problem is he uses two hard disks with his PC, so there's something conflict. I check the common bugs in the forum and found a solution for this. Now he's checking out Ubuntu and he seems to like it.

Sorry for not checking through the forum first.
Cheers for all your helps! :D

---

