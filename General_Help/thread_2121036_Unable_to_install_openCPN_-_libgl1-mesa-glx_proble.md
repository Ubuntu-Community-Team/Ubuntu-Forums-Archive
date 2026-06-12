---
title: "Unable to install openCPN - libgl1-mesa-glx problem"
date: 2013-02-28
forum: General Help
---

### Post by FuzzyFeat on 2013-02-28
When I try to install opencpn.deb  (a marine chart ploter) using the ubuntu software center, i get the message "cannot install 'libgl1-mesa-glx' ".
 
My graphics card is a Mobility Radion 3650, (ATI RV635).  I show no proprietary drivers listed in the System Settings/Additional Drivers/ and when queried in the Terminal, it shows the vid card as an unknown type.

I have previoulsy used opencpn with 12.04 and had no problems installing opencpn. This is a fresh re-install of 12.04. The system has been updated.

Thanks,

---

### Post by FuzzyFeat on 2013-03-10
bump

---

### Post by FuzzyFeat on 2013-03-21
I found a work-around. 

First i went to:
[https://launchpad.net/~opencpn/+archive/opencpn]("https://launchpad.net/~opencpn/+archive/opencpn") for the PPA

Opened my terminal, added the ppa -

```
 :~$ sudo add-apt-repository ppa:opencpn/opencpn
```

Bunch of stuff

```
:~$ sudo apt-get update
```
more stuff

```
:~$ sudo apt-get install opencpn
```

Installs openCPN

At the prompt - type:
```
~$ opencpn
```

OR

Go to unity, type in opencpn, the icon will appear and ---- 



Bob's your uncle.


Worked for me. Just tried it out this morning.

---

### Post by FuzzyFeat on 2013-03-23
[solved] :-)

---

### Post by aneblanc on 2014-01-22
It worked for me too, thanks, Thierry

---

