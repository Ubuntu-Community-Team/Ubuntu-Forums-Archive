---
title: "aaarrggghhhhhh - it wont go away"
date: 2006-07-08
forum: General Help
---

### Post by metricben on 2006-07-08
i cant uninstall openoffice2

i messed up openoffice so reinstalled openoffice2 - it is a differeent version than what i had before(older), and crashes whenever i try to open anything.

i cant uninstall it!!!

i have 'openoffice2' installed and all components
i believe i should install 'openoffice'(without the 2)

this is urgent as i need to complete some work and do not want to go on a windoze box

tell me how to delete this annoying software from my pc.](*,) 
actually i love openoffice

anyway thx

---

### Post by Rui Pais on 2006-07-08
Hi,
have you try on a terminal:
```
sudo apt-get -f install
```
to solve the broken packages.

---

### Post by bruce89 on 2006-07-08
The latest package for OpenOffice.org is called just OpenOffice.org, not OpenOffice.org2.  OOo2 was for when it was still unstable.

---

### Post by metricben on 2006-07-08
```
ben@benspc:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
ben@benspc:~$

```

i believe this has something to do with the fact theat if i "fix broken packages" without anything selected, nothing happens: it is only with the problematic openoffice2 (which i have no idea why they dont remove it)

> it was still unstable

well that figures

---

### Post by Rui Pais on 2006-07-08
At synaptic, pressing 'Custom' button (on left bottom) gives you access to Broken (2nd on le list after All) 

Can you fix it from there?

Another option is trying to uninstall with aptitude. 
aptitude usually deals with dependencies better then apt or synaptic.

---

### Post by metricben on 2006-07-08
omg thank you so much, i selected the relevant packages and went to custom (never knew what that was) then broken.  after uninstalling the southafrican(???) and english language packs which were broken, i could uninstall openoffice2.

this all started when i installed the spanish language pack so there is probably some link...
:-D:-D:-D

---

### Post by Rui Pais on 2006-07-08
> **metricben said:**
> :-D:-D:-D

Glad to know it works!

Have fun, bye.

---

### Post by metricben on 2006-07-08
yep, installed "openoffice.org" and everything is working fine

thank you

---

