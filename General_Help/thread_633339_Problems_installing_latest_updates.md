---
title: "Problems installing latest updates"
date: 2007-12-06
forum: General Help
---

### Post by justinjacobs on 2007-12-06
Has anyone else experienced problems with the latest updates for Gusty? Update Manager fails to complete the update and reports broken dependencies related to **libpango1.0-dev**. I try to run **sudo apt-get install -f**, but that fails as well. Here's the output when I try to run that:

```
justin@justin-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libqt0-ruby1.8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpango1.0-dev
Suggested packages:
  libpango1.0-doc
The following packages will be upgraded:
  libpango1.0-dev
1 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.
4 not fully installed or removed.
Need to get 0B/359kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by erfahren on 2007-12-06
this may not help much, but see: [http://ubuntuforums.org/showthread.php?t=508679](http://ubuntuforums.org/showthread.php?t=508679)

I'd try: sudo dpkg-reconfigure -a first.

---

### Post by justinjacobs on 2007-12-06
Thanks for the suggestion. But I think I found the main problem I was having. In /var/lib/dpkg/status on line 8623, there was this:
```
libfontconfig1-dev (>= ¬\ã¢	R)
```
I took the wild risk of deleting it. However, everything seems to be working fine now. If I recall correctly, I remember having dependency problems in the past with libfontconfig. Keeping my fingers crossed that my computer doesn't blow up at some point. :-P

---

