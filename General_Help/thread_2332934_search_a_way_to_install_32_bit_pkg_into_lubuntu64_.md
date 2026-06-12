---
title: "search a way to install 32 bit pkg into lubuntu64 16.04"
date: 2016-08-05
forum: General Help
---

### Post by oui on 2016-08-05
[SOLVED]

is that possible?

what is to do?


(which pkg: in my case, it would be "xvidcap", but I am interesting with the general answer to that question!)

---

### Post by Dennis N on 2016-08-05
The general answer is 'yes'. You can run 32-bit software on a 64-bit OS. With Ubuntu, you first enable installation of 32-bit software with a dpkg command, and then you are able to easily install such packages:
```
sudo dpkg --add-architecture i386
```
When both 64 and 32 bit packages are available, the 32-bit packages use the ending :i386 - for example, firefox:i386

---

### Post by oui on 2016-08-05
Hi Dennis N

It works! Thank you very much!

---

