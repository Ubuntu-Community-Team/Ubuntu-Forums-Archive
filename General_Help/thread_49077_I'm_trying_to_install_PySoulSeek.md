---
title: "I'm trying to install PySoulSeek"
date: 2005-07-14
forum: General Help
---

### Post by Noah0504 on 2005-07-14
I'm trying to install PySoulSeek, which is a Linux client for the file sharing program SoulSeek.

I'm extremely new to Linux, and I'm really not sure where to begin.  I tried downloading the RPM package, but I don't think ubuntu supports them, because the only option I received was to extract it.  I downloaded the source but I'm not sure how to compile it.  I read the readme and it gave a set of instructions for just running it, but I get some error for wxpython.

Any help would be thanked.

Here is a link to the PySoulSeek website:  [http://www.sensi.org/~ak/pyslsk/](http://www.sensi.org/~ak/pyslsk/)

---

### Post by Mike Buksas on 2005-07-15
I don't believe that there is anyway to use rpms with Ubuntu, since Ubuntu is based on Debian and it's apt pacakge management system. (Corrections on this point welcome!)

You can get wxpython via apt, however. Try

```
sudo apt-get wxpython2.5.3
```

and see if that clears up the error you're seeing. This version is for python2.4. Apt should also install it, if you don't have it already, since it is a dependency of wxpython2.5.3. 

Mike

---

### Post by Noah0504 on 2005-07-15
[QUOTE=Mike Buksas]I don't believe that there is anyway to use rpms with Ubuntu, since Ubuntu is based on Debian and it's apt pacakge management system. (Corrections on this point welcome!)

You can get wxpython via apt, however. Try

```
sudo apt-get wxpython2.5.3
```

and see if that clears up the error you're seeing. This version is for python2.4. Apt should also install it, if you don't have it already, since it is a dependency of wxpython2.5.3. 

Mike[/QUOTE]
 Well, I found out how to convert RPMs to DEB packages.  That really didn't help me though, haha.

I downloaded wxpython, however, I need the latest version and not 2.5.3.  I looked at the wxpython website, but the installation looks beyond my skill level.

---

### Post by angkor on 2005-07-15
Don't know anything about PySoulseek but I use nicotine as my soulseek client:

sudo apt-get install nicotine

---

### Post by Noah0504 on 2005-07-16
[QUOTE=angkor]Don't know anything about PySoulseek but I use nicotine as my soulseek client:

sudo apt-get install nicotine[/QUOTE]
 Thanks!  Nicotine is actually built from PySoulSeek.

---

### Post by angkor on 2005-07-16
Welcome :) 
Didn't know that...

---

