---
title: "missing source.list"
date: 2006-07-23
forum: General Help
---

### Post by TheRingmaster on 2006-07-23
when I do a sudo kwrite /etc/apt/source.list, kwrite comes up blank! Same happens with Kate. Is this normal?:-?

---

### Post by Ziox on 2006-07-23
do:
cat /etc/apt/sources.list
in terminal

and if nothing comes up, then that's not normal. So if you need a copy of it, i can provide you one...

---

### Post by TheRingmaster on 2006-07-23
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ dapper-backp
```

This is what it gives me. But why does it not show when I do a ```
sudo kwrite /etc/apt/source.list
```

---

### Post by Ziox on 2006-07-23
try this command instead: kdesu kwrite /etc/apt/sources.list

EDIT: i noticed that you did source.list, instead of source**s**.list that's probably why...simply but common mistake

---

### Post by deanjm1963 on 2006-07-23
it is " sources.list " NOT source.list

that might help

---

### Post by Jagot on 2006-07-23
It's sources.list - not source.list - plural!

```
sudo kwrite /etc/apt/sources.list
```

---

### Post by Landoln on 2006-07-23
> **jpazindustries said:**
> 
This is what it gives me. But why does it not show when I do a ```
sudo kwrite /etc/apt/source.list
```

because you put source.list instead of sources.list.   put that 's' back in there and it should work fine.

EDIT: looks like two or three people beat me to it while I was posting.  ah well, you get the point then :)

---

### Post by TheRingmaster on 2006-07-23
oops!!!!!!! My bad :oops:

---

