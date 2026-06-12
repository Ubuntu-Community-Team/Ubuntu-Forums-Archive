---
title: "Getting the Executor Macintosh emulator to work"
date: 2006-07-21
forum: General Help
---

### Post by j5tixc on 2006-07-21
Hello! Back when I was using Windows I frequently used the Macintosh emulator called Executor. I have some old Mac games I used to play. But since I switched to (K)Ubuntu I haven't been able to play them. :( In the past I've tried getting the Linux version of Executor working but I haven't been able to.

Anyways, now I've decided to really try to make it work. The problem is that the packages are in RPM format. There is a demo version in a deb package though.

Since I don't know how to get it installed myself I thought I'd ask on this great forum. So can anybody here succesfully install and run Executor on Linux?

[ftp://ftp.ardi.com/pub/Executor_Linux/](ftp://ftp.ardi.com/pub/Executor_Linux/)
[ftp://ftp.ardi.com/pub/Executor_Linux/OLD](ftp://ftp.ardi.com/pub/Executor_Linux/OLD)

Is it even possible? It would be great if someone managed because I really want to play my Mac games.

---

### Post by slimdog360 on 2006-07-21
you can convert the rpm packages into deb format by using alien. I ssume you dont have alien so to get get use the following
```
sudo aptitude install alien
```
then to turn the packages into deb format you can just use the code ```
sudo alien packagename.rpm
```
from there to install by deb use the following
```
sudo dpkg -i packagename.deb
```

---

### Post by j5tixc on 2006-07-22
> **slimdog360 said:**
> you can convert the rpm packages into deb format by using alien. I ssume you dont have alien so to get get use the following
```
sudo aptitude install alien
```
then to turn the packages into deb format you can just use the code ```
sudo alien packagename.rpm
```
from there to install by deb use the following
```
sudo dpkg -i packagename.deb
```

Thank you. Yes I've heard about alien. I just downloaded it and tried to install the packages but it seems like it's not being installed in the right location because I still can't start it from the console etc.

---

### Post by j5tixc on 2006-08-06
Weird, weird, weird. I still can't get it to work. I'm not even sure which files I should install! It just throws some pointless error message at me when I try to start it.

---

