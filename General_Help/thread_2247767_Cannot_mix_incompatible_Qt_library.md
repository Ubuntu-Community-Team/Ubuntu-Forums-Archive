---
title: "Cannot mix incompatible Qt library"
date: 2014-10-10
forum: General Help
---

### Post by tigerjack89 on 2014-10-10
Hi guys. 
I've founded a lot of similar problems on the web, but still no real solution.
I'm having the annoying


    Cannot mix incompatible Qt library (version 0x40806) with this library (version 0x40802)


message whenever I try to launch **genymotion**.
It seems that the problem is either in environment variables or different libraries installed. So, I'm trying to see the output of various commands


1. ```
echo $LD_LIBRARY_PATH

```returns nothing (actually there is no environment variable with this name.


2. ```
echo LD_LIBRARY_PATH=. ldd ./genymotion
```and [this is the output]("http://pastebin.com/v784bRHM")

3. ```
dpkg -al | grep libqt
```
returns [this]("http://pastebin.com/c70XNgt8")


4.```
$>qmake --version
QMake version 3.0
Using Qt version 5.2.1 in /usr/lib/x86_64-linux-gnu

```

Any idea?

---

### Post by tigerjack89 on 2014-10-10
Problem solved using the solution posted at this link
[http://ubuntuforums.org/showthread.php?t=2207219&p=13048000#post13048000](http://ubuntuforums.org/showthread.php?t=2207219&p=13048000#post13048000)

---

### Post by sammiev on 2014-10-10
Good find. Should mark this one as solved, I'm sure it will help others. ;)

---

### Post by tigerjack89 on 2014-10-10
> **sammiev said:**
> Good find. Should mark this one as solved, I'm sure it will help others. ;)
sure, just done :)

---

