---
title: "ubuntu clashing with windows errors 0,0"
date: 2013-10-12
forum: General Help
---

### Post by acepro71 on 2013-10-12
ok i recently was able to install ubuntu and when i downloaded some stuff in it and booted back to windows 

and open the file it says its being used .... windows cant access it .... i cant even delete it from windows

i can open and use the file in ubuntu and its a jpeg file..

---

### Post by Rob Sayer on 2013-10-12
It doesn't sound like it's 'clashing'.  When you install ubuntu it creates a linux partition formatted in ext4 format.  Windows can't read this format.  However, linux can read/write any disc formats that windows uses.  Try copying the file over to your windows partition.

---

### Post by philinux on 2013-10-12
> **acepro71 said:**
> ok i recently was able to install ubuntu and when i downloaded some stuff in it and booted back to windows 

and open the file it says its being used .... windows cant access it .... i cant even delete it from windows

i can open and use the file in ubuntu and its a jpeg file..

Is this a regular install or is it. Wubi?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by acepro71 on 2013-10-12
its a regular install ...

---

### Post by acepro71 on 2013-10-12
> **Rob Sayer said:**
> It doesn't sound like it's 'clashing'.  When you install ubuntu it creates a linux partition formatted in ext4 format.  Windows can't read this format.  However, linux can read/write any disc formats that windows uses.  Try copying the file over to your windows partition.

yes its an ext4 partition but i saved the files on other partition which is ntfs

---

### Post by philinux on 2013-10-12
> **acepro71 said:**
> yes its an ext4 partition but i saved the files on other partition which is ntfs

Did you hibernate windows and then boot into ubuntu?

---

### Post by acepro71 on 2013-10-12
> **philinux said:**
> Did you hibernate windows and then boot into ubuntu?

maybe i cant tell as its windows 8 it was easy telling that with windows 7 

but i always click shut down though


but its opening the windows partition so that means it isn&#8217;t hibernated 

if it was ubuntu wont open it

---

