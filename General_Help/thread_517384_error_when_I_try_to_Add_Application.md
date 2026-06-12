---
title: "error when I try to Add Application"
date: 2007-08-04
forum: General Help
---

### Post by sigurdkaare on 2007-08-04
Hi everybody!

I got a problem when I try to add a new application in "Add/Remove Application"

I get this error:

"An error occured

The following details are provide

E: /var/cache/apt/archives/liba52-0.7.4_0.7.4-7_i386.deb: files list file for package `gnome-mime-data' is missing final newline"


Do anybody know what is is wrong and what I can do about it?

---

### Post by apswartz on 2007-08-04
You get this error with every application you try to install or just the one?

---

### Post by apswartz on 2007-08-04
try this command...
```
sudo apt-get clean
```

then try again.

---

### Post by sigurdkaare on 2007-08-04
I got the error with every application.

But now I have re-installed ubuntu and it alle works fine! :guitar:

Thanks for your time!

Sigurd

---

### Post by apswartz on 2007-08-04
hehehe, the I guess you can go ahead and mark this thread as SOLVED.

---

