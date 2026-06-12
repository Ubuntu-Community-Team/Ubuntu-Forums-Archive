---
title: "apt segfaults"
date: 2007-11-24
forum: General Help
---

### Post by Apreche on 2007-11-24
I'm using my computer normally. Nothing is weird. Everything works just fine. I was apt-getting some php packages earlier in the day with no problems. Just now I decide to apt-get some other package to try it out. Now, every apt related command produces segfaults except for apt-get update.
```
apreche@danuba:~$ sudo apt-get update
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
...
```
```
apreche@danuba:~$ aptitude search foo
Segmentation fault (core dumped)
```
```
apreche@danuba:~$ synaptic
Segmentation fault (core dumped)
```
```
apreche@danuba:~$ sudo apt-get install foo
Reading package lists... Done
Segmentation fault (core dumped)
```

What am I supposed to do about this?

---

### Post by r00tintheb0x on 2007-11-24
A. Have you tried upgrading your distro to something crazy, like Debian to Ubuntu?

B. Have you tried using strace to see if you can figure it out. 

C. Have you run apt/aptitude with the -v flag so you can see whats going on?

r00t

---

### Post by Apreche on 2007-11-25
> **r00tintheb0x said:**
> A. Have you tried upgrading your distro to something crazy, like Debian to Ubuntu?No, it's a clean Gutsy install with nothing weird.

> B. Have you tried using strace to see if you can figure it out. [Here is a link to the strace](http://www.apreche.net/~apreche/strace.txt).

> C. Have you run apt/aptitude with the -v flag so you can see whats going on?
```
root@danuba:/home/apreche# aptitude -v search foo
Segmentation fault (core dumped)
root@danuba:/home/apreche# apt-get -v install foo
apt 0.7.6ubuntu14 for i386 compiled on Oct 15 2007 20:39:10
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file
root@danuba:/home/apreche# 
```

---

### Post by Apreche on 2007-11-26
I hate bumping threads, but I'm really hanging out to dry here. If I can't fix it, I'll have to reinstall :(

---

### Post by Apreche on 2007-11-27
OK, Explain this one. I get home today, and the orange star icon is in my system tray. apt works again with no problems. 

WTF.

---

