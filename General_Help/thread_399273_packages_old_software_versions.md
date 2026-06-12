---
title: "packages: old software versions"
date: 2007-04-02
forum: General Help
---

### Post by stephan0h on 2007-04-02
Hello,
1st post in this group. I use ubuntu 6.10.
Some deb-packages point to old versions of software that are already some months of age. I've experienced this now a number of times and maybe there is a solution 
that I'm unaware of. 2 recent examples:

kino: ubuntu - 0.9.0 ... 1.0.0 already available
qdvdauthor: ubuntu 0.1.2 ... 0.1.5 already available

What can I do to obtain the current versions of software. (Of course I could download it directly, but I would rather stick with debian packages ...)

regards,
stephan

---

### Post by Majorix on 2007-04-02
Well the thing is that once caught a stable state, developers won't update to the newer versions of software. As such, since 6.10 is already stable there won't be too many upgrades to it, only those that are found to be strictly necessary will be done.

If you want the newest software why don't you try out 7.04 BETA?

---

### Post by stephan0h on 2007-04-02
is there a way to use packages of newer ubuntu-releases, where the software is up-to-date without the need to upgrade the whole system? or is it even possible for me to "refresh" the packages with the respective software versions? i wonder: there must be an "easy" way to achieve this ...

---

### Post by az on 2007-04-02
You want a backported version of the software.  Enable the backport repository and see if someone has already backported the software.

---

### Post by WW on 2007-04-02
A similar question was recently asked here: [http://ubuntuforums.org/showthread.php?t=397940](http://ubuntuforums.org/showthread.php?t=397940)
This is probably in a FAQ somewhere, too.

If you really need the latest version, sometimes the only alternative is to get the source code and compile it yourself.

If you search [http://packages.ubuntu.com](http://packages.ubuntu.com) , you'll see that even feisty only has version 0.92 of kino, so don't expect a backport of kino 1.0 any time soon.

---

### Post by stephan0h on 2007-04-03
Thanks for the hints on packages and backports, now I know where to go with my wishes for new versions :-)

---

