---
title: "edgy-multiverse.list error"
date: 2007-02-21
forum: General Help
---

### Post by oppilif.fm on 2007-02-21
i get a error after adding net repo but i have tryed to remove the new repo i added to fix the problem but i still get it if anyone can help please 

E: The line 2 in /etc/apt/sources.list.d/edgy-multiverse.list (dist parse) is incorrect
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


thanks for any help

---

### Post by Maestro23 on 2007-02-21
> **oppilif.fm said:**
> i get a error after adding net repo but i have tryed to remove the new repo i added to fix the problem but i still get it if anyone can help please 

E: The line 2 in /etc/apt/sources.list.d/edgy-multiverse.list (dist parse) is incorrect
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


thanks for any help

Open a terminal, and post the output:

> cat /etc/apt/sources.list

---

### Post by oppilif.fm on 2007-02-22
io@io-laptop:~$ cat /etc/apt/sources.list
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
io@io-laptop:~$

---

### Post by taurus on 2007-02-22
The problem is not with your /etc/apt/sources.list.  It's your /etc/apt/sources.list.d/edgy-multiverse.list.

```
cat /etc/apt/sources.list.d/edgy-multiverse.list
```
Or put a # in front of line 2 in /etc/apt/sources.list.d/edgy-multiverse.list to comment it out.

```
gksudo gedit /etc/apt/sources.list.d/edgy-multiverse.list
```

---

### Post by oppilif.fm on 2007-02-25
nothing i try and i get the same error to line 3 and if i do the same thing to line 3 i get the same error to line 4 it wont read it i really don t know how to fix this problem

---

### Post by taurus on 2007-02-25
Can you at least post your file here?

```
cat /etc/apt/sources.list.d/edgy-multiverse.list
```

---

