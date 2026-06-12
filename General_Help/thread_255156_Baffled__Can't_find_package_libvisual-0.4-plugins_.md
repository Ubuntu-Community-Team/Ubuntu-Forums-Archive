---
title: "Baffled:  Can't find package libvisual-0.4-plugins in repos"
date: 2006-09-11
forum: General Help
---

### Post by Paradoxdruid on 2006-09-11
I'm..  baffled.  I've upgraded to Amarok 1.4.3 using the instructions at [http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php) , but I can't for the life of me FIND the package **libvisual-0.4-plugins** to install for dapper (I've found an edgy source).  I have libvisual-0.4-0 , and it mentions libvisual-0.4-plugins, but no repository I've found has it.

What repository is missing from my sources.list?
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free 
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted 

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe 
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb http://security.ubuntu.com/ubuntu dapper-security universe 
deb-src http://security.ubuntu.com/ubuntu dapper-security universe 

#ntfs-3g & fuse-2.5 repo:
deb http://flomertens.keo.in/ubuntu/ dapper main
deb-src http://flomertens.keo.in/ubuntu/ dapper main

#amarok 1.4.3
deb http://kubuntu.org/packages/amarok-143 dapper main
```

Thank you in advance for any help!

---

### Post by alonso on 2006-09-11
Hi, 

this seems to be a bug in repositories. It works, if I have both 1.4.2 and 1.4.3 repositories enabled:


```

#amarok 1.4.3
deb http://kubuntu.org/packages/amarok-143 dapper main
deb http://kubuntu.org/packages/amarok-142 dapper main

```

-al

---

### Post by Paradoxdruid on 2006-09-11
Thanks for the help, alonso, that does seem to be on the right track.

It now finds libvisual-0.4-plugins, but says ```
libvisual-0.4-plugins: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
```and according to apt-get, I have the latest libpango1.0-0. Any further ideas?

---

### Post by Paradoxdruid on 2006-09-12
just one *bump*

I still haven't figured out how to resolve these dependencies.  Gah.  Thanks for any help/ideas!

---

