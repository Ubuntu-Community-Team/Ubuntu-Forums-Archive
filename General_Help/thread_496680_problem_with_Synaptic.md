---
title: "problem with Synaptic"
date: 2007-07-09
forum: General Help
---

### Post by laplie on 2007-07-09
every time I start synaptic package manager I get the following error:

E: Unable to write mmap - msync (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

and then it exits.  What does this mean and how can I fix it?

---

### Post by Rui Pais on 2007-07-09
hi,
have you run out of free space on disc?
Whats the output of:
```
df -h /
```?

---

### Post by laplie on 2007-07-09
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             181G   17G  155G  10% /

```

---

### Post by Rui Pais on 2007-07-09
do you have a separated /var partition?

---

### Post by laplie on 2007-07-09
/var is on the same partition.

The error started happening right after I uninstalled MySQL from synaptic

---

### Post by Rui Pais on 2007-07-09
Thats an hard one.
Usually mmap/msync errors are due to no free space on disc. Not your case obviously...

Have you tried do:
```
sudo apt-get install -f
```

If you think is related with mysql you can try purge it:
```
sudo aptitude purge mysql-*
```

and/or try to re-install it by download packages [from here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mysql-&searchon=names&subword=1&version=feisty&release=all") and install them with dpkg -i (and hoping that dpkg work... and this is just an apt problem)

Apart from that i'm without ideas.

Good luck.

---

### Post by laplie on 2007-07-09
> **Rui Pais said:**
> Thats an hard one.
Usually mmap/msync errors are due to no free space on disc. Not your case obviously...

Have you tried do:
```
sudo apt-get install -f
```

If you think is related with mysql you can try purge it:
```
sudo aptitude purge mysql-*
```



I ran those 2 commands and it fixed it.  It was probably something with mysql.

Thanks a lot, Ubuntu 4 ever, these forums are the best, down with the establishment, etc, etc.

---

### Post by Rui Pais on 2007-07-09
> **laplie said:**
> I ran those 2 commands and it fixed it.  It was probably something with mysql.

Thanks a lot, Ubuntu 4 ever, these forums are the best, down with the establishment, etc, etc.

:)
at that point i was more shooting in the dark then anything else :p
 
Glad it's working

---

