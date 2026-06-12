---
title: "Software Index is Broken!"
date: 2007-07-05
forum: General Help
---

### Post by geovino on 2007-07-05
A friend of mine is having trouble installing programs. she's using Feisty. She gets this message:
"Software Index is Broken. Impossible to install or remove any software"

What would cause this and how can we fix it?

I installed Automatix when I installed Feisty last month. Everything has been working until this happened.

---

### Post by kosmic on 2007-07-05
Ok to fix this problem in a terminal type :


```

sudo apt-get install -f

```

---

### Post by geovino on 2007-07-06
> **kosmic said:**
> Ok to fix this problem in a terminal type :


```

sudo apt-get install -f

```

Thanks! that did the trick :p

Problem Solved.

---

### Post by ramadhian on 2007-07-07
rama@rama-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgoocanvas-common
The following NEW packages will be installed:
  libgoocanvas-common
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0B/24.5kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 176216 files and directories currently installed.)
Unpacking libgoocanvas-common (from .../libgoocanvas-common_0.6-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libgoocanvas-common_0.6-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/locale/en_GB/LC_MESSAGES/goocanvas.mo', which is also in package gpredict
Errors were encountered while processing:
 /var/cache/apt/archives/libgoocanvas-common_0.6-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This problem happened when I try to install package "Conduit" from [http://www.getdeb.net](http://www.getdeb.net)
"File goocanvas.mo" belong to package gpredict, then I try to remove gpredict and delete file goocanvas.mo manually ,,, 

the same error msg still appear ,, 

What Should I do now ,, I can not update package or install any package any more ,,

Please SomeBody Help Me ,, :o

---

