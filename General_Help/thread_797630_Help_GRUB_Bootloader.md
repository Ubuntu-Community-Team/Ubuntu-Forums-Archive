---
title: "Help: GRUB Bootloader"
date: 2008-05-17
forum: General Help
---

### Post by Paris Heng on 2008-05-17
Dear,

My Hard disc now got 2 type of OS, one is Ubuntu, one is MS Windows. I recently delete the Ubuntu partition using LIVE CD GParted. So, it only have the NTFS. When I restart and load, it show error for GRUB. I can't load into the Windows. After that, i try re-install back the Ubuntu, then I will able to have the GRUB menu. 

How to delete the GRUB bootloader together with the Ubuntu. I believe my problem is cause by the previous installed GRUB bootloader that still reside in the BIOS. 

Please give some help.

---

### Post by the8thstar on 2008-05-17
Okay, your assumption is correct. Even though you erased Ubuntu, the Grub was still in the MBR, so Windows couldn't start.

Since you have Ubuntu reinstalled, you can use Grub to launch Windows. But first we need to know "where" it is, so that we can instruct Grub to look for it correctly.

So, in the terminal, type:
[B]> 
sudo fdisk -l[/B]

and paste the result in your next post. We'll go from there then.

---

### Post by ajgreeny on 2008-05-17
Or if you do not want to keep Ubuntu you can simply reinstall the windows MBR with the windows CD which you should have.  If you don't have one download one of the many restore MBR utilities you can find on google.  I think the Supergrub disk will do it for you.

---

### Post by Flare183 on 2008-05-17
Kinda tricky if you do it that way. But there is also another way. That is to backup everything that you want/need off the hard drive onto a removable storage device. And take the Windows Install CD and reformat the entire hard drive. Which gets rid of everything including GRUB. This may suck but I can't help that.

---

### Post by strabes on 2008-05-17
If you do not wish to keep ubuntu, you can follow the instructions [here](http://pcpropaganda.wordpress.com/2007/08/09/fixing-windows-xp-master-boot-record-mbr/), assuming you have a windows CD available.

---

### Post by Paris Heng on 2008-05-21
> **strabes said:**
> If you do not wish to keep ubuntu, you can follow the instructions [here](http://pcpropaganda.wordpress.com/2007/08/09/fixing-windows-xp-master-boot-record-mbr/), assuming you have a windows CD available.

Thank alot!!! It works.

---

