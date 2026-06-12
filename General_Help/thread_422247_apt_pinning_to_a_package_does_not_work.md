---
title: "apt pinning to a package does not work"
date: 2007-04-25
forum: General Help
---

### Post by novosirj on 2007-04-25
I can't get this to work, and it's slowly driving me nuts. Here is my /etc/apt/preferences file:

Package: tora
Pin: release a=now
Pin-Priority: 999

The result is this with apt-cache policy:

root@novosirj-laptop:/var/lib/dpkg# apt-cache policy tora
tora:
  Installed: 1.3.21-3ubuntu1
  Candidate: 1.3.21-3ubuntu1
  Package pin: 1.3.21-3ubuntu1
  Version table:
     1.3.21-3ubuntu1 999
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
 *** 1.3.21-3ubuntu1 999
        100 /var/lib/dpkg/status

...clearly the pin-priority is ending up at the end of the version number. Why? Who knows. Watch this though:

root@novosirj-laptop:/var/lib/dpkg# cat /etc/apt/preferences
Package: *
Pin: release a=now
Pin-Priority: 999

root@novosirj-laptop:/var/lib/dpkg# apt-cache policy tora
tora:
  Installed: 1.3.21-3ubuntu1
  Candidate: 1.3.21-3ubuntu1
  Version table:
     1.3.21-3ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
 *** 1.3.21-3ubuntu1 0
        999 /var/lib/dpkg/status

This time it worked. The name of the package is tora, there's nothing wrong with /var/lib/dpkg/status as far as the package name is concerned (I thought maybe the package name might have ended up as "tora " or something).

The only thing strange about the tora package is that I too a deb-src package and I changed it to build including Oracle. 

I really have no idea what's going on -- I followed the documentation. HELP! :)

---

