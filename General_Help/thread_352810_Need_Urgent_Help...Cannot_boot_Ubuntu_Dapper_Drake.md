---
title: "Need Urgent Help...Cannot boot Ubuntu Dapper Drake"
date: 2007-02-03
forum: General Help
---

### Post by magichsjx on 2007-02-03
Hello. First time poster here and a newbie with a small big problem:) 

I am running a dual boot system with windows millennium and ubuntu installed on the same drive (hda). It has 4 partitions (FAT32) and the primary partition hodls windows and one of the extended partitions the ubuntu dapper drake 6.0.6 LTS.

Now, everything was going smoothly until I used, under windows,  GAG47, which is a boot manager, thinking I could always uninstall it as the documentation said. I had installed ubuntu manually after win me and modified the menu.list so that windows booted first and then I had enough time to boot ubuntu if I wanted to. As it turned out, Gag did not recognize ubuntu, only windows and so I had to uninstall it but now I think it has changed my MBR so that I cannot boot ubuntu at all. My boot record seems messed up. I tried all the forum posts to no avail.

I tried the Live CD and booted from that, mounted my ubuntu partition on root (/) and could see that the swap partition was still there and I think the rest of the software should be there even though I could not access anything as I was obviously not logged in as the user I was with the installed version.

My question is, can I adjust the MBR so that it can boot ubuntu. Do I have any option but to reinstall ubuntu. I would appreciate help on this. Thank you in advance.:(

---

### Post by Shay Stephens on 2007-02-03
Let this be a lesson to all.  Don't let windows or windows programs mess with the hard drive.  They are narcissistic in the fact they see nothing but themselves.  If you want to manage, do it in linux.

That said, try restoring the grub menu with the install cd:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Let us know if that worked for you :)

---

