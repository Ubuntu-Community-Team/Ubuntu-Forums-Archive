---
title: "GCC on ubuntu"
date: 2008-03-06
forum: General Help
---

### Post by abc7887 on 2008-03-06
is there any way to compile c progs on ubuntu ....and is there gcc compiler on ubuntu?

---

### Post by taurus on 2008-03-06
Yes, there is a gcc compiler for Ubuntu.  You just need to install the build-essential package first.

```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

---

### Post by chewearn on 2008-03-06
```
sudo aptitude install build-essential
```and you are good to go.

EDIT:
Rats!  Seconds too late.[SIZE=1]*:biggrin:*[/SIZE]

---

### Post by abc7887 on 2008-03-06
thanx mate..

---

