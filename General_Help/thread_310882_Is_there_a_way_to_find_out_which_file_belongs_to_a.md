---
title: "Is there a way to find out which file belongs to a package"
date: 2006-12-02
forum: General Help
---

### Post by yusufg on 2006-12-02
Hi, Is there a way to find out which package a file belongs to in Ubuntu

in rpm based distros I could do rpm -qif </path/to/file> and it would tell me which package it was from

What is the equivalent in deb based distros ?

---

### Post by cptnapalm on 2006-12-02
sudo dpkg -S filename

---

### Post by jr.gotti on 2006-12-02
"apt-file"

man it but i believe it's just "apt-file [filename]"

---

### Post by jf/ on 2007-09-02
> **jr.gotti said:**
> "apt-file"

man it but i believe it's just "apt-file [filename]"
doesn't seem to work here. Not 'apt-file search $filename' either. Is there a proper way to call this up so that it behaves properly as expected?

I've tried the following, for example:
```

apt-file --package-only search `which bash`
apt-file --package-only search bash
apt-file -x --package-only search '.*bash.*'
apt-file list bash

```

all of which give empty output. Does apt-file work at all?

---

### Post by capink on 2007-09-03
before using apt-file to search you must run:

```
sudo apt-file update
```

this will take sometime

then you can run

```
apt-file search /path/to/the/file
```

---

### Post by jf/ on 2007-09-03
> **capink said:**
> before using apt-file to search you must run:

```
sudo apt-file update
```


uh?!! I would have thought that this would have been done for me already. But thanks...

---

