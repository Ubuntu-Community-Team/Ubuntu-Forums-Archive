---
title: "MySQL 6.0 Installation"
date: 2008-05-14
forum: General Help
---

### Post by bpinkston on 2008-05-14
I compiled, made, and installed MySQL 6.0 - alpha, with 5.0 installed. 

I didn't realize, that 5.0 was installed in /usr/share, and 6.0  configuration by default installed into /usr/local.  How can I rectify this situation.  I have located both of the bin, lib, and language directories, as well as knowing where the 5.0 startup files are in /etc. I have considered backing up and copying the 6.0 files over the 5.0 files.  will this work?  If so, does anyone know what changes have to be made in etc., and with apparmor?

---

### Post by macaholic on 2008-05-14
So what exactly is your problem? Are the tow conflicting in some way? Please clarify.

---

### Post by bpinkston on 2008-05-14
Sorry I wasn't clear.  I am a relative rookie to Linux, and how services (daemons) etc.. work.  

Right now 5.0 is the running database, (it works fine) and I just want to replace it with 6.0.  Which I already installed but inadvertantly to a different directory. 

Thanks,

---

### Post by Monicker on 2008-05-14
Just remove mysql 5.0 via the Ubuntu package management, and let mysql 6.0 run from where it installed to.

---

### Post by bpinkston on 2008-05-14
Would you happen to know where I could find resources on how to configure app armor for the other installation.

---

