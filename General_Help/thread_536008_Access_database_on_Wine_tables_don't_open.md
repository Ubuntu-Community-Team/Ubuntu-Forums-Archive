---
title: "Access database on Wine: tables don't open"
date: 2007-08-27
forum: General Help
---

### Post by clara_9 on 2007-08-27
I installed Office 2000 (Feisty, Wine) and got around the problem of missing IE by installing it as well and a couple of missing dll-files which I just copied from my old windows computer into the windows directory of wine.
So far so good. Now I can actually open my existing MS Access mdb-file... and then everything stops, since I can't open any of the tables. 

As far as I see the following error keeps on coming up:

err:ole:CoGetClassObject class {039ea4c0-e696-11d0-878a-00a0c91ec756} not registered
err:ole:CoGetClassObject class {039ea4c0-e696-11d0-878a-00a0c91ec756} not registered
err:ole:CoGetClassObject no class object {039ea4c0-e696-11d0-878a-00a0c91ec756} could be created for context 0x3

Any ideas?

Or alternatives? I also tried to use OpenOffice but for some reason that seem to delete the primary key out of all the tables, turning the whole database useless.
And I tried installing MS Office using Cross Office but that wasn't able to install from my Office CD.

---

### Post by clara_9 on 2007-08-29
SOLVED

I got it solved in the end. 
(1) getting a different copy of the Office 2000 files, and installing it again using Cross Office. I had used a nicely hacked and patched Office 2000 copy before. 

(2) RESTARTING Ubuntu. Contrary to claims that there would be no reason to restart a Linux computer. A restart brought up the newly installed Cross Office files properly and working.

---

