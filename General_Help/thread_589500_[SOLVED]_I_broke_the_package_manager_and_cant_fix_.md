---
title: "[SOLVED] I broke the package manager and cant fix it (7.04)"
date: 2007-10-24
forum: General Help
---

### Post by weblordpepe on 2007-10-24
I deleted a file because the package manager crashed & I couldn't open a new one.
I forgot what file I deleted, but now I get this whenever I run any package management program:

> root@davobug:/home/pepe# apt-get check
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing language-pack-be (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
root@davobug:/home/pepe# 
 Help! I don't know what to do and I want to upgrade to the next wine. :(

---

### Post by UK-Wobbie on 2007-10-24
> **weblordpepe said:**
> I deleted a file because the package manager crashed & I couldn't open a new one.
I forgot what file I deleted, but now I get this whenever I run any package management program:

 Help! I don't know what to do and I want to upgrade to the next wine. :(

All i can say is to backup your work on to a CD or DVD... And upgrade to 7.10 may fix it!
Or do a new start with the 7.10 ISO Image. ](*,);):lolflag::guitar::mrgreen:\\:D/

---

### Post by weblordpepe on 2007-10-24
](*,) aahhh nooooo. although yeah im doing that anyway. i just want to upgrade wine in the time being.

i actually messed with drivers so much that i just want to wipe everything & start fresh with 7.10.

---

### Post by ukripper on 2007-10-24
This blog may help [http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/](http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/)

---

### Post by UK-Wobbie on 2007-10-24
> **weblordpepe said:**
> ](*,) aahhh nooooo. although yeah im doing that anyway. i just want to upgrade wine in the time being.

i actually messed with drivers so much that i just want to wipe everything & start fresh with 7.10.

A fresh start with 7.10  is a good start if you keep on messing with the drives :lolflag::lolflag:

---

### Post by weblordpepe on 2007-10-24
> **ukripper said:**
> This blog may help [http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/](http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/)Wow it worked thanks very much!

---

### Post by ukripper on 2007-10-24
i am glad it worked out for you...Keep us updated how you progress with Gutsy, my experience with gutsy was just incredible as my acer laptop battery power increased from 30 mins to 2 hours..Hail to Gutsy kernel!! Things are also much faster on it than my previous Edgy. 

Hope you'll also be as delighted as me after upgrad/ fresh install!

---

