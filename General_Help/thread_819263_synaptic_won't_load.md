---
title: "synaptic won't load"
date: 2008-06-05
forum: General Help
---

### Post by mccartryan on 2008-06-05
Recently I noticed this problem with trying to open a synaptic.  I have no idea how it came about, but when I try to load the package manager I get the following error message:

E: Type '"deb' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open()failed, please report

Can anyone help me fix this problem?

---

### Post by forestpixie on 2008-06-05
Run this command in a terminal

```
cat /etc/apt/sources.list
```

Post the output here, you need to edit the file, or

**Edit** - the file will have lines that start with either

#
deb
deb-src

anything else will cause an error, if you can see where the error/s are from the cat command - then edit it - bakcup first

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.0506
```

open to edit

```
gksudo gedit /etc/apt/sources.list
```

make sure line start with #, deb or deb-src - if you have lines saying #deb-src or #deb leave them

run this command to update 

```
sudo apt-get update
```

If that means nothing to you - post the output :)

---

### Post by mrMango on 2008-06-05
Obviously, on line 56 in the file /etc/apt/sources.list you have a syntax error.

---

### Post by mccartryan on 2008-06-05
Worked great!  Thanks for the help!

---

