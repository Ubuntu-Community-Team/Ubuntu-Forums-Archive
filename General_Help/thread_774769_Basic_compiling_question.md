---
title: "Basic compiling question"
date: 2008-04-29
forum: General Help
---

### Post by s3a on 2008-04-29
I want to compile something (cinelerra-2.1-src.tar.bz2) from source. Tell me what in the following is wrong:

Steps:

1) cd ~/Desktop/temp
2) ./configure
3) make
4) sudo make install

**Do I have to do something before "./configure" and after "cd ~/Desktop/temp"?**

---

### Post by Oldsoldier2003 on 2008-04-29
> **s3a said:**
> I want to compile something (cinelerra-2.1-src.tar.bz2) from source. Tell me what in the following is wrong:

Steps:

1) cd ~/Desktop/temp
2) ./configure
3) make
4) sudo make install

**Do I have to do something before "./configure" and after "cd ~/Desktop/temp"?**
*Did you untar the source files? then you need to change into the new directory and run ./configure*
a default installation of Ubuntu requires that you

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

it also doesn't hurt to see if you can get the build dependencies for the package you are trying to build. (they are not always available this way but when they are its a big time and trouble saver.

```
sudo apt-get build-dep <package-name>
```

---

