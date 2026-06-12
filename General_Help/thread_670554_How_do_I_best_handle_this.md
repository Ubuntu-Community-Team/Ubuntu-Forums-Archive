---
title: "How do I best handle this?"
date: 2008-01-17
forum: General Help
---

### Post by bdemers on 2008-01-17
This is a new installation of 7.10 workstation.  During attempt to install an app (Medusa4), the message given below displayed:


Starting the installer...
med/run/csginst: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


I really don't have that file, but I do have libstdc++.so.6 and the library that that file points to.  I assume that lib....so.5 is a predecessor of .so.6, but not certain.  How do I handle this?  Fix the installation file?, create a .so.5 with the contents of .so.6 in it? Not aware of the implications.  I think that the root of the issue is with the installation routine not being aware of the version change, if that's what happening. I don't want to set myself up for hassles in the future, though, so I'm hands off until I hear something from you folks.

Thanks a bunch!!!

---

### Post by ahaslam on 2008-01-17
Try:
```
sudo apt-get install libstdc++5
```

---

### Post by bdemers on 2008-01-17
As you suggested, I tried, but failed, to install ...so.5.  Couldn't find the file.  Sorry.  Problem is I'm so new at this that even the obvious eludes me.

---

### Post by ahaslam on 2008-01-18
I'm guessing it's installed, but missing a link, unless there was an error during installation?
Open a terminal & enter:
```
cd /usr/lib && ls libstdc*
```
This should produce something like:
```
libstdc++.so.5  libstdc++.so.5.0.7  libstdc++.so.6  libstdc++.so.6.0.9
```
If you have 'libstdc++.so.5.0.7' listed but no *.so.5 you can create a link:
```
cd /usr/lib && sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5
```
Any closer?

---

### Post by bdemers on 2008-01-18
I repeated "sudo apt-get install libstdc++5" in terminal and this time I succeeded.  Perhaps I typo'd first time around, who knows.  Anyway, thanks for your help!.

---

