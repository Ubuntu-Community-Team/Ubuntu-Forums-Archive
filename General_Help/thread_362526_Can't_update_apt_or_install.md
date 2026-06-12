---
title: "Can't update apt or install"
date: 2007-02-15
forum: General Help
---

### Post by rannasjem on 2007-02-15
When every I try to use add/remove programs or run apt update from the terminal I get at error.

E: Malformed line 6 in source list /etc/apt/sources.list (dist parse)

my first couple lines in sources.list are

# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted #Added by software-properties


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

---

### Post by meng on 2007-02-15
At the end of line 6, add the words
"main restricted"

---

### Post by rannasjem on 2007-02-15
thanx meng, works fine now

---

