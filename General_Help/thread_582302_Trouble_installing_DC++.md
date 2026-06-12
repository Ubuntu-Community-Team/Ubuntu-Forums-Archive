---
title: "Trouble installing DC++"
date: 2007-10-19
forum: General Help
---

### Post by Bleakesth on 2007-10-19
Hi there, i'm a complete novice with ubuntu so apologies if this has been discussed before.
I'm trying to install dc++, and i've gotten as far as having the linuxdcpp folder in my home folder, but when I try to compile it I get the following error message:

~/linuxdcpp$ sudo scons install
Password:
scons: Reading SConscript files ...

scons: *** Error writing options to file: build/sconf/scache.conf
[Errno 2] No such file or directory: 'build/sconf/scache.conf'
File "/home/paddy/linuxdcpp/SConstruct", line 68, in <module>

Can anyone help? It would be much appreciated, i'm desperate to get the wonderful DC++ working on ubuntu!

---

### Post by Bleakesth on 2007-10-20
*Bump*

Surely someone knows what to do here?

---

### Post by jocko on 2007-10-20
It seems the linuxdcpp/build/ directory is missing.
I tried to get a fresh copy of linuxdcpp from cvs, but got the same problem as you (fortunately I have a working copy...).

You could try to fix it this way:
1. Download the three attached .tar.gz files (they contain the contents of my linuxdcpp/build/ directory).
2. Make a directory named "build" in your linuxdcpp directory.
3. Unpack the .tar.gz files into linuxdcpp/build.
You should now have three subdirectories under build/:
client/
gui/
sconf/

4. Now try to build and install again:
```
cd ~/linuxdcpp
scons release=1 PREFIX=/usr/local
sudo scons install
```

You may need to notify the linuxdcpp developers about this to get it fixed.

---

### Post by Gargamella on 2007-10-20
I installed the deb package if you are interested :

[http://www.getdeb.net/app.php?name=Linux+DC%2B%2B](http://www.getdeb.net/app.php?name=Linux+DC%2B%2B)


Even if I prefear nicotine, this is a nice app

---

### Post by Bleakesth on 2007-10-20
> **jocko said:**
> It seems the linuxdcpp/build/ directory is missing.
I tried to get a fresh copy of linuxdcpp from cvs, but got the same problem as you (fortunately I have a working copy...).

You could try to fix it this way:
1. Download the three attached .tar.gz files (they contain the contents of my linuxdcpp/build/ directory).
2. Make a directory named "build" in your linuxdcpp directory.
3. Unpack the .tar.gz files into linuxdcpp/build.
You should now have three subdirectories under build/:
client/
gui/
sconf/

4. Now try to build and install again:
```
cd ~/linuxdcpp
scons release=1 PREFIX=/usr/local
sudo scons install
```

You may need to notify the linuxdcpp developers about this to get it fixed.
The same problem keeps happening, but thanks for your help all the same.

---

### Post by Bleakesth on 2007-10-20
> **Gargamella said:**
> I installed the deb package if you are interested :

[http://www.getdeb.net/app.php?name=Linux+DC%2B%2B](http://www.getdeb.net/app.php?name=Linux+DC%2B%2B)


Even if I prefear nicotine, this is a nice app
It worked, woohoo! Christ, why didn't I just do this in the first place? I'm a total novice, that's why! Thank you muchly, you have made my day!

---

### Post by stevensheehy on 2007-10-20
I've fixed the issue on my local copy. It wasn't missing the build dir, just accessed it before it was created. I'll commit it soon.

---

