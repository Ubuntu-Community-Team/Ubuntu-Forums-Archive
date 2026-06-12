---
title: "Help... grub error.. browsing from cell phone"
date: 2006-11-18
forum: General Help
---

### Post by zer0efx on 2006-11-18
I ran into a problem with my grub loading. I have ubuntu on a sep physical drive and xp on my main c drive. I was prepping my c drive for a fresh vista install so I used pm8 to partition the drive... I restarted so it could do its thing and upon restarting I get this error:

Grub loading stage1.5

Grub loading, please wait...
Error 17

I can't get into xp or ubuntu so I'm not sure how to fix this error. I can use my roommates comp to make a bootdisk for grub, if someone could point me in the right direction?

sorry to be so short... but I am on my cell phone.

Thanks for any help

---

### Post by catlett on 2006-11-18
If you overwrote the mbr, this should fix it. [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) All you need is the Ubuntu Live  installation cd.

---

### Post by cotcot on 2006-11-18
Check your /boot/grub/menu/lst.
See if the root of the ubuntu partition is correct and check if the file system of the partition is the same as in the menu.
Maybe PM has changed partition numbers.

---

### Post by zer0efx on 2006-11-18
> **catlett said:**
> If you overwrote the mbr, this should fix it. [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) All you need is the Ubuntu Live  installation cd.

Thanks a lot!!!
IT worked great! (Posting from Windows)

---

