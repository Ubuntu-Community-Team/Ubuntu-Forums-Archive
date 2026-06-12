---
title: "MySQL Not Autostarting"
date: 2007-08-31
forum: General Help
---

### Post by yahooadam on 2007-08-31
Hi

When i first installed MySQL it would autostart with the computer, However, for some reason it has stopped working on my server

How do i get mysql to autostart ? 
i tried chmod +x /etc/init.d/mysql
i also tried update-rc.d mysql start

How do i get mysql to start with ubuntu :(

Thanks in advance
Yahooadam

---

### Post by apetresc on 2007-08-31
It might be that MySQL is *trying* to start, but failing for some reason. Does it work when you do ```
sudo /etc/init.d/mysql start
```?

---

### Post by scxtt on 2007-08-31
do you have something like:

S##mysql -> ../init.d/mysql

in /etc/rc2.d . . . ?

---

### Post by yahooadam on 2007-08-31
> **AdrianP said:**
> It might be that MySQL is *trying* to start, but failing for some reason. Does it work when you do ```
sudo /etc/init.d/mysql start
```?
Yes it works fine starting it manually - except i then have to restart mythtv because mysql was down (i dont know if having mythtv effects it - i should have said)

> **scxtt said:**
> do you have something like:

S##mysql -> ../init.d/mysql

in /etc/rc2.d . . . ?
in /etc/rc2.d i have "S20mysql"
Inside that file is a whole load of code (196 lines)

I also looked in /var/log mysql.err and mysql.log
Their both empty

---

### Post by swegoof on 2007-10-04
Hi there Yahooadam,

I'm experienceing the same problems as you are... at least you had them. Did you ever got around it? Did you find out what was wrong, and how to fix it?

And most important... is it working fine now? ;)

TIA
//swegoof

---

### Post by yahooadam on 2007-10-04
Its working orite for me now, but i think im a few re-installs down the line (HDD corruptions)

I dont know why it does it, but you can use somthing like monit to keep it going
Ofcourse, setting that up can be a pain in the a$$ too

---

