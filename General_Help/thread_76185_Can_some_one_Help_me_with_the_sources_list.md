---
title: "Can some one Help me with the sources list?"
date: 2005-10-14
forum: General Help
---

### Post by dpkg on 2005-10-14
HEy some one can post me the regular source list of the last version please i have alot of problam with mys till i changed the file
so please if can do me a favore i will be happy.


sorry my english is too bad :|

---

### Post by egorgry on 2005-10-14
This is mine I hope you find it helpfull. 
```
#deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

#mplayer and other goodies
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#E17
deb http://ubuntu.nooms.de/ hoary/

```

---

### Post by Leif on 2005-10-14
these

```
#mplayer and other goodies
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#E17
deb http://ubuntu.nooms.de/ hoary/
```

are _not_ part of the regular repositories, and while useful, could cause problems.

---

### Post by egorgry on 2005-10-14
[QUOTE=Leif]these

```
#mplayer and other goodies
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#E17
deb http://ubuntu.nooms.de/ hoary/
```

are _not_ part of the regular repositories, and while useful, could cause problems.[/QUOTE]
Thanks Leif, good looking out. I should have mentioned that I like to play. :) I've been a debian unstable user for 5 years and like to hack. ubuntu is too easy to use I have to make it interesting.

---

### Post by dpkg on 2005-10-14
Thanks for the quick help but it's dosn't work, I must get the new file like after the installation 5.10 please guys.

---

### Post by Leif on 2005-10-14
go here : [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes), scroll down, and there's a pristine source list. if you have any problems, let us know what.

p.s. I noticed egorgry's list had non-ubuntu stuff, but not that it's all for hoary !

---

### Post by dpkg on 2005-10-14
Yes!!! THanks it's work awsome!

---

### Post by Leif on 2005-10-14
[QUOTE=egorgry]Thanks Leif, good looking out. I should have mentioned that I like to play. :) I've been a debian unstable user for 5 years and like to hack. ubuntu is too easy to use I have to make it interesting.[/QUOTE]

it's nice to have some "old-timers" using ubuntu as well as the newbs like me. me, I disabled marillat straight after installing the codecs I needed.

---

### Post by manicka on 2005-10-14
[QUOTE=Leif]these

```
#mplayer and other goodies
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#E17
deb http://ubuntu.nooms.de/ hoary/
```

are _not_ part of the regular repositories, and while useful, could cause problems.[/QUOTE]

The marillat repo _will_ break your system, don't use it.

---

