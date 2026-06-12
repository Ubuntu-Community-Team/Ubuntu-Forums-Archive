---
title: "I cant install anything!"
date: 2006-12-11
forum: General Help
---

### Post by jcrnan on 2006-12-11
I tried to install xwinwrap with these commands as it said on beryl-project.org

cvs -d server:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cd xwinwrap
make


This seemed to work but xwinwrap commands didnt work so I gave up on it. then I later tried installing stuff but it wont work because it thinks xwinwrapcvs is corrupted and it refuses to do anything until that is fixed and I have no idea how to fix it.


andre@laptop:~$ sudo aptitude purge xwinwrapcvs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be automatically REMOVED:
xwinwrapcvs{p}
The following packages will be REMOVED:
xwinwrapcvs{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing xwinwrapcvs (--purge):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
what(): basic_string::_S_construct NULL not valid
Errors were encountered while processing:
xwinwrapcvs
Aborted (core dumped)
andre@laptop:~$




andre@laptop:~$ sudo aptitude install rar-free
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "rar-free". However, the following
packages contain "rar-free" in their name:
unrar-free
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the xwinwrapcvs package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
andre@laptop:~$



I also can't use the update thing or install from .deb's.

Please help!

---

### Post by goatflyer on 2006-12-11
I'm betting you never installed xwinwrap from synaptic or apt --- all you did was check out a copy of the source with cvs.  If I'm right, in such a case its no wonder that apt/aptitude/synaptic/ knows nothing about that package and is therefore powerless to remove it.

Just cd to your xwinwrap directory, go up one level and delete the directory.  Like this:

```

cd ..
rm -r xwinwrap

```

So, was I right? :)

---

### Post by hanzomon4 on 2006-12-11
Open up synaptic, then open the edit menu and select fix broken packages

---

### Post by jcrnan on 2006-12-12
I deleted anything called xwinwrap. I also repaired any broken packages. Still same errors :(

---

### Post by hanzomon4 on 2006-12-12
Try this command ```
sudo dpkg --configure -a
```

---

### Post by jcrnan on 2006-12-15
hanzomon: That seemed to fix it at first but then the same errors came back when I tried installing something.

---

