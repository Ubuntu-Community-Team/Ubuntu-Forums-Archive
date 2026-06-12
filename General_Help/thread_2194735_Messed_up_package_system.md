---
title: "Messed up package system"
date: 2013-12-20
forum: General Help
---

### Post by Charobnjak on 2013-12-20
Hi,

I have a problem with a messed up package system on ubuntu 13.10. It seems to have been caused by a filesystem coruption because of a loosly pluged-in cable. 

Synaptic reports that all of my packages have broken depedecies while sofware center just says there's a problem and gives me an empty list of packages with broken dependecies,

Is there a way to fix this or will I have to reinstall ubuntu?

Thanks.

---

### Post by deadflowr on 2013-12-20
Have you tried
```
sudo apt-get install -f
```
?

---

### Post by Charobnjak on 2013-12-20
Yeah, it gave me this: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies

---

### Post by deadflowr on 2013-12-20
Try cleaning and refreshing the package list
```
sudo apt-get clean
sudo apt-get update
```
then try the install -f(fix broken packages command) again.
If any errors come out during the update command, post them.

---

### Post by Charobnjak on 2013-12-20
It's fixed :D

-f didn't even have to do anything, thanks a lot, I really thought that I would have to reinstall it.

---

