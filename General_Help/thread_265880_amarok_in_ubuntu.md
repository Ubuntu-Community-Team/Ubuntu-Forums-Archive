---
title: "amarok in ubuntu"
date: 2006-09-26
forum: General Help
---

### Post by galanos on 2006-09-26
Hi

I've just upgraded to dapper and I'm having problems installing amarok.
I have ubuntu and not kubuntu and I'm not getting anywhere.something about not being able to install libvisual-0.4-0...

Can I install amarok without swiching to kubuntu? if so how? anybody have the same problem? Is this even going to be possible?
Any suggestions welcome...

---

### Post by doggie on 2006-09-26
put this line in your sources file (/etc/apt/sources.list)..

#Amarok 1.4.3
**deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main**

then in the terminal just
[B]
sudo apt-get update
sudo apt-get install amarok[/B]

that's how i did it and it's working... it's gonna install a lot of libs. and stuff from kde

---

### Post by aysiu on 2006-09-26
Sounds as if you have a bad sources.list.

I would [get a fresh one](http://www.psychocats.net/ubuntu/sources) and then try again: ```
sudo aptitude update
sudo aptitude install amarok
``` As doggie says, though, it will install a lot of libraries.

---

### Post by galanos on 2006-09-26
Thanks both of you but:

-Doggie : I've tried that already many (many) times but I get back a message:
Failed to fetch [http://kubuntu.org/packages/amarok-143/dists/dapper/main/binary-powerpc/Packages.gz](http://kubuntu.org/packages/amarok-143/dists/dapper/main/binary-powerpc/Packages.gz)  403 Forbidden
when I try to get it via synaptic, it tells me that amarok depends on libvisual-0.4-0, which it refuses to install ("uninstallable")

aysiu : i tried what you suggested, but my computer does'nt recognize the command "aptitude"...

---

### Post by galanos on 2006-09-26
Ok I finally was able to download amarok, but it's the 1.3.9 version, not the 1.4.3...

hmmm, I'll work on it some more

---

### Post by doggie on 2006-09-26
do you have dapper-backports enabled in your sources list ??
can you see this page [http://kubuntu.org/packages/amarok-143/](http://kubuntu.org/packages/amarok-143/) without any problem ??

403 error is so f@#½&ng rare :confused: :-k

---

