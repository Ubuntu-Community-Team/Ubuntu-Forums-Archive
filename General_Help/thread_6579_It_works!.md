---
title: "It works!"
date: 2004-11-29
forum: General Help
---

### Post by Infatuated_iPod on 2004-11-29
As i sit here writing this i am shocked that i am actually on this forum using linux! This is the first time i have ever gotten ubuntu to work for me at all. I can not believe that i am on here! I have not ever tried to run ubuntu on this computer but still, i am amazed. Everything runs very smoothly, and i couldnt be happier. There is actually nothing wrong!!! Sound works, network works.. this is a first, when i has suse 9.0 on this computer absolutely nothing worked!!! Thanks ubuntu! This definantly makes my day ! :)

---

### Post by adbak on 2004-11-29
Ubuntu is next to godliness.

---

### Post by BWF89 on 2004-11-29
The only probem I've had with Linux (atleast the live cd's) is getting my printer and scanner to work. It detects they it's a Cannon printer but it can't detect that it's an S520 series...

---

### Post by zenwhen on 2004-11-29
The Ubuntu LiveCD was the first one I have tried that gave me sound on every computer I tried it on.

---

### Post by arctic on 2004-11-30
[QUOTE=BWF89]The only probem I've had with Linux (atleast the live cd's) is getting my printer and scanner to work. It detects they it's a Cannon printer but it can't detect that it's an S520 series...[/QUOTE]
the problem with the canon printer is not only causing headaches to ubuntu users but linux-users in general. there is no module for this yet in the kernel, but i do know that there is some "home made module" available for this printer somewhere on the web. you will still need the devel tools in order to add it to your box. 

i just stumbled over this one: [http://www.linuxprinting.org/pipermail/canon-list/2003q2/000976.html](http://www.linuxprinting.org/pipermail/canon-list/2003q2/000976.html)
maybe it helps you. they are talking of a rpm, but as far as i know, you can convert an an rpm to a .tar.gz  or .deb file somehow. there should be a howto for that somewhere, too.

---

### Post by adbak on 2004-11-30
[QUOTE=arctic]
i just stumbled over this one: [http://www.linuxprinting.org/pipermail/canon-list/2003q2/000976.html](http://www.linuxprinting.org/pipermail/canon-list/2003q2/000976.html)
maybe it helps you. they are talking of a rpm, but as far as i know, you can convert an an rpm to a .tar.gz  or .deb file somehow. there should be a howto for that somewhere, too.[/QUOTE]
I believe the program Alien should be installed by default on your computer, if not, download and install it.

To convert from RPM to DEB:
```
alien -d <insert filename>.rpm
```
Voilà.  Then just install the .deb ```
dpkg -i <insert filename>.deb
```
and you're good to go.

---

### Post by arctic on 2004-12-01
thanx for the "alien" info. *one more lesson learned today* :)

---

### Post by jdong on 2004-12-02
Yep, alien is a wonderful tool! I usually use it the other way -- getting .debs into rpms, because I prefer the .deb-way of building packages as opposed to rpm SPEC's.


Note that when converting, -d is implied by default -- no need to put it on.

---

