---
title: "Apt missing packages"
date: 2006-07-11
forum: General Help
---

### Post by Archform on 2006-07-11
I am not a noob to linux but to debian/ubuntu I am having the hardest time. I ran gentoo as my primary box till very recently. I was impressed by the ease of use of this distro. The problem that I have been having is that things that the documentation says should be there are not in APT. I have been trying to get fcgi installed and fluid and both, which are listed in documentation on the ubuntu site, are missing and I have no idea how to add them or even get them to install.  I am running the 6.06 desktop.

Any suggestions would be most helpful

---

### Post by nanotube on 2006-07-11
both libfcgi and fluid are in the universe repository. the universe repository is not enabled by default. 

easiest way to do it is to go into synaptic, select settings>repositories (or something of that nature) from the menu, and there you can check the checkbox for universe, and while you are at it check the one for multiverse, too.

that will greatly expand the amount of packages available to you.

---

### Post by jordilin on 2006-07-11
or just edit the file in /etc/apt/sources.list and add this line 
```
deb http://es.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```
Then apt-get update and you will be able to see the package in synaptic

---

### Post by Archform on 2006-07-11
Nanotube you are the Awesomest... thanks for the tip.. as soon as I get home I will do it... 

Thanks again

P.S. thanks jordilin also that let me do it from work

---

