---
title: "Wubi 8.04 Vista issue"
date: 2008-02-05
forum: General Help
---

### Post by Bowxoxo on 2008-02-05
Hi, I am new to wubi. I have a vista laptop and I just install the new wubi 8.04 rev398. After the install is complete and the computer reboots. In boot menu when I click on ubuntu it shows that \ubuntu\winboot\wubildr.mbr is not found. 

I check the the winboot forder there is only menu in there, anyone know how I can get that file??

Thanks

---

### Post by Sciophobia on 2008-02-05
Just happened to me too with 398, 396 was last working revision I tried.

EDIT: If you get daring, use 7-Zip to open the 396 exe and you can extract the files you need, haven't tried it yet.  Here's everything that was in the folder.

---

### Post by kungmo on 2008-02-06
I want to install wubi on my vista laptop. but I can't even run it.
Are you using vista business edition? (I use business edition)
Could you please write what your vista edition is?

---

### Post by Bowxoxo on 2008-02-06
> **kungmo said:**
> I want to install wubi on my vista laptop. but I can't even run it.
Are you using vista business edition? (I use business edition)
Could you please write what your vista edition is?




I am using Vista Ultimate...and my laptop is Toshiba Qosmio (core 2 dual T7200) if you also woundering. I used to use the 7.04 wubi version and that one works fine on my computer.

---

### Post by Bowxoxo on 2008-02-06
> **Sciophobia said:**
> Just happened to me too with 398, 396 was last working revision I tried.

EDIT: If you get daring, use 7-Zip to open the 396 exe and you can extract the files you need, haven't tried it yet.  Here's everything that was in the folder.

Thanks, I will play with it later and see if that will do anything.:)

---

### Post by ago on 2008-02-06
Yes use 396 or 397, 398 is missing some files, my fault, I will fix it tonight.

---

### Post by ago on 2008-02-06
> **ago said:**
> Yes use 396 or 397, 398 is missing some files, my fault, I will fix it tonight.

398 is fine now

---

### Post by Bowxoxo on 2008-02-06
> **ago said:**
> 398 is fine now

Thanks ago :)

---

### Post by eatfleshnow on 2008-02-27
I actually have this same issue. The C drive is my windows install and the M drive is a separate hard drive where I placed the Ubuntu installation. 

I checked for that file and it appears to be right where its supposed to be.

I've tried the latest version of wubi(431) with no success. Let me know if theres any other information I should add, I'm very much looking forward to trying Ubuntu as this would be my first time!

---

### Post by ago on 2008-02-27
440 is the latest version, try uninstalling and reinstalling.
[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

It might also be that grub cannot see your m drive, in which case you might want to try the other drive.

---

### Post by eatfleshnow on 2008-02-27
Thank you! That at least got Ubuntu to start! I encountered an error that said something about the install failing but thats probably an issue for a different area of this forum.

Thanks again!

---

