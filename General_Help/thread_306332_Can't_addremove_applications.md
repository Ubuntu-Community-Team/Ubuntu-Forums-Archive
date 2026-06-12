---
title: "Can't add/remove applications"
date: 2006-11-24
forum: General Help
---

### Post by happysmileman on 2006-11-24
Whenever I try to add or remove a program I get the following error message:

dpkf: parse error, in file `/var/lib/dpkg/available' near line 2569 package `procps':
   `Conflicts field, reference to `w-bassman': version contains `)'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

When I go to line 2569 in `/var/lib/dpkg/available' I see the following:

Conflicts: watch, libproc-dev (<< 1:1.2.6-2), w-bassman (<< (5îR-3), procps-nonfree, pgrep (<< 3.3-5)

I am assuming that the `(<< (5îR-3)' should be (<< version number)... How am I suppose to fix this... it appeared to happen when i installed xmms and/or xine player

---

### Post by happysmileman on 2006-11-24
In a file in /var/backup I see a similar line with w-bassman (<< 1.0-3)... Would it fix it if I simply replaced the version number

---

### Post by happysmileman on 2006-11-25
Ok I'm bumping this because it's gone to the 5th page

---

### Post by depu on 2006-11-27
apparently your dpkg database is corrupted. 
All you need to do is reload the old file , i thinks its in the same directory as status , it'll be called status-old(just check before you run this)
so simply sudo cp  /var/lib/dpkg/status-old /var/lib/dpkg/status

just in case this doesnt work make sure that you backup the corrupted db

sudo cp  /var/lib/dpkg/status-old /var/lib/dpkg/status-imade

---

