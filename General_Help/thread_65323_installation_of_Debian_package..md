---
title: "installation of Debian package."
date: 2005-09-13
forum: General Help
---

### Post by impeteperry on 2005-09-13
I have downloaded a .dep package from the Debian web site
 qt3-designer_3.3.4-3_i386.deb
and being net to Ubunto, how do I install it?

Thanks for the help.

---

### Post by sethmahoney on 2005-09-13
sudo dpkg -i name-of-file

---

### Post by krusbjorn on 2005-09-13
sudo dpkg -i  qt3-designer_3.3.4-3_i386.deb

---

### Post by impeteperry on 2005-09-13
[QUOTE=krusbjorn]sudo dpkg -i  qt3-designer_3.3.4-3_i386.deb[/QUOTE]
Thanks, I tried this and got
```
root@ubuntu:/home/pete/Desktop # sudo dpkg -i qt3-designer_3.3.4-3_i386.deb
(Reading database ... 117733 files and directories currently installed.)
Preparing to replace qt3-designer 3:3.3.4-3 (using qt3-designer_3.3.4-3_i386.deb) ...
Unpacking replacement qt3-designer ...
dpkg: dependency problems prevent configuration of qt3-designer:
 qt3-designer depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 qt3-designer depends on libqt3c102-mt (>= 3:3.3.4); however:
  Version of libqt3c102-mt on system is 3:3.3.3-7ubuntu3.
dpkg: error processing qt3-designer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 qt3-designer
root@ubuntu:/home/pete/Desktop #
``` 
Apparently I already had it. I had been searching under "QtDesigner", not "designer". will try to get it up and running.
Thanks

---

### Post by impeteperry on 2005-09-13
I had been searching for QtDesigner not designer. here is what I found searching for designer"

usr/lib/kde3/plugins
usr/lib/qt3/plugins
usr/share/qt3/tools

I am lost as to what to do with these. Please help.
Thanks

---

### Post by impeteperry on 2005-09-13
I found the designer. It was in the /usr/bin directory which the "Find  Files/Folders" utility DID NOT FIND. It found designer files in /usr/share/qt3 directory but not in the /usr/bin directory. I went back to my Fedora Core 3 computer and ran the "Find Files/Foulders" and found the file. I then, in a terminal, went to the /usr/bin direceory and typed "designer" and up it came. I then put a "link" to it on my desktop. 

Is this a bug?

Thanks for all your help anyway.

---

### Post by psychicdragon on 2005-09-14
I'm confused.

Why are you trying to install a package from the debian ftp site?

```
sudo apt-get install qt3-designer
```

---

### Post by impeteperry on 2005-09-14
It was a misteake. The results of "Find Files/Folders"  for "designer" did not find it!! 
It found the stuff in /usr/bin, /usr/share & /usr/KDE but not in /usr/bin where it was. 
I had to go to my old computer where "Find Files/Folders" found it in "/usr.bin". 
Not knowing what to do, I put a link to it on the "desktop". It runs fine from there except it can't find some of the needed plugins which probably are the ones in the /usr/lib/qt3. 

I don't know how to put them in the path, but I am working on it

Thanks

---

