---
title: "[SOLVED] Changing CD-ROM to Ubuntu Sites"
date: 2008-06-18
forum: General Help
---

### Post by gamingneeds on 2008-06-18
Hey, I'm trying to install LAMP on my server but when running the install it is asking me to put in the install CD. How do I redirect it so it will look at the Ubuntu web site instead?

Thanks.

---

### Post by nikgare on 2008-06-18
You need to go to:

System->Adminstration->Software Sources

and remove the CDROM optin in either the "Ubuntu Software" tab or "Third Party Sotware" tab

Nik

---

### Post by gamingneeds on 2008-06-18
Forgive me, but I am lost.

This is server based, so I do not have options of that nature that I am aware of.

How can I do this via SSH/FTP?

Thanks.

---

### Post by nikgare on 2008-06-18
You need to edit /etc/apt/sources.list and comment out the references to cdroms

Nik

---

### Post by gamingneeds on 2008-06-18
I deleted:


# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted


form the source.list file as instructed and when I tried installing again, it WORKED.

Thanks for your help!

---

