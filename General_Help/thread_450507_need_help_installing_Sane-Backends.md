---
title: "need help installing Sane-Backends"
date: 2007-05-21
forum: General Help
---

### Post by juniorsonny on 2007-05-21
I downloaded sane-backends-1.0.18.tar.gz and need help installing it.

---

### Post by juniorsonny on 2007-05-21
I downloaded sane-backends-1.0.18.tar.gz and need help installing it. Please somebody Help!!!!!!!

---

### Post by dexter on 2007-05-21
You a shot here:
- unpack it
- open a terminal and go to the folder where you unpacked
- type ./configure (may not be necessery)
- type ./make
- type ./make install (possible as sudo)

If configure/make isn't recognized as a program you'll need to install build essentials:
```
sudo apt-get install build-essentials
```

---

### Post by juniorsonny on 2007-05-21
It lets me ./configure but I can't ./make or ./make install......It says no file or directory found.   I also tried to    sudo apt-get install build-essentials   but it said it couldn't find the file.

---

### Post by juniorsonny on 2007-05-21
I'm using Feisty does this make a difference?

---

### Post by juniorsonny on 2007-05-21
Help any Ideas?

---

### Post by juniorsonny on 2007-05-21
Please Help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by rbmorse on 2007-05-22
There should be a text file named *install* within the tarball.  Might be helpful to take a look at that.

---

