---
title: "magical disappearing files"
date: 2006-08-24
forum: General Help
---

### Post by lapsey on 2006-08-24
when i tried apt-get update i am greeted with 

```
E: The method driver /usr/lib/apt/methods/http could not be found.
```

yet

/etc/apt appears totally unmolested:

```
-rw-r--r-- 1 root root   70 2006-08-22 14:49 /etc/apt/apt.conf
-rw------- 1 root root    0 2006-08-22 14:41 /etc/apt/secring.gpg
-rw-r--r-- 1 root root  546 2006-08-20 14:25 /etc/apt/sources.list
-rw-r--r-- 1 root root    0 2006-08-22 14:41 /etc/apt/sources.list~
-rw------- 1 root root 1200 2006-08-22 14:41 /etc/apt/trustdb.gpg
-rw-r--r-- 1 root root 2393 2006-08-22 14:41 /etc/apt/trusted.gpg
-rw-r--r-- 1 root root 2381 2006-08-22 14:41 /etc/apt/trusted.gpg~

/etc/apt/apt.conf.d:
total 2
-rw-r--r-- 1 root root  80 2006-04-03 15:44 05aptitude
-rw-r--r-- 1 root root 182 2006-05-15 12:49 70debconf

/etc/apt/sources.list.d:
total 0
```

also, /opt/nicotine/ is almost empty:

```
-rw-r--r-- 1 root root 35 2005-12-18 16:16 /opt/nicotine/Makefile
```

when before it has all the program files in it.


The filesystem is ext3, the drive is new enough to have automatic badblock checking on it, so i ask: what the heck just happened to it?

I haven't touched it until i tried to use apt-get and before, all was hunky dory. I'm behind a nat'd router, no ports are open, and the vnc password is different from the user password.

it's crazy!

---

