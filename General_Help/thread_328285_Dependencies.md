---
title: "Dependencies"
date: 2006-12-30
forum: General Help
---

### Post by Buck2348 on 2006-12-30
I know dependencies are a common problem, but since I've been reading in this forum I haven't seen an answer to this.  I tried today to install Gnome Commander, downloading the source from nongnu.org.  When I tried to compile it, it gave four dependencies it needed.  You can guess where it went from there--I got 3 or 4 levels deep and gave up.  When I went back to the homepage and found where they kept their binary packages, I downloaded and installed a .deb in about a minute.  How can one ever get a source package from outside the depositories installed?  And how do they make a relatively small .deb package satisfy all those dependencies?

Thanks,
Buck

---

### Post by angkor on 2006-12-30
Welcome to the old world! :) 

Installing from source can be a hassle when a program has a lot of dependencies. The trick is to learn to search for the dependencies more easily, for example with 
'apt-file search [file-name-your-missing]'

However, next time you can try to build dependencies first before compiling the program. This only works if the program is in the repositories.

```
sudo apt-get build-dep [package-name]
```


Edit: Maybe you wanted to install a newer version, if not, gnome-commander is in the repos. You can install version 1.2.0-3.1 with:

```
sudo apt-get install gnome-commander
```

---

### Post by dothedorky on 2006-12-30
Thank you angkor, i've been having the same problem!8)

---

