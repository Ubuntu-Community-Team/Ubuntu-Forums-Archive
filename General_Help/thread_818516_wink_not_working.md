---
title: "wink not working"
date: 2008-06-04
forum: General Help
---

### Post by Pawlicki on 2008-06-04
new install of unbuto 8.04 - I install wink and when I try to run it I get this error:
====
/usr/lib/wink/wink: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
====
I tried to install the missing file but libexpat.so.0 is not in the repositories

Is there a fix. Anyone using wink with 8.04?

thanks

---

### Post by ibutho on 2008-06-04
You need to install expat using the packaging tools e.g.
```
Menu -> Accessories -> Terminal
sudo aptitude update
sudo aptitude install expat

```
If expat is already installed, can you post the output of running
```
sudo find /usr/lib -name "*expat*"
```

---

### Post by Pawlicki on 2008-06-05
Same problem here is the result of running
find /usr/lib -name "*expat*"
==
root@john-laptop:/home/john# find /usr/lib -name "*expat*"
/usr/lib/libexpat.so.1.5.2
/usr/lib/python2.5/lib-dynload/pyexpat.so
/usr/lib/python2.5/xml/dom/expatbuilder.pyc
/usr/lib/python2.5/xml/dom/expatbuilder.py
/usr/lib/python2.5/xml/sax/expatreader.pyc
/usr/lib/python2.5/xml/sax/expatreader.py
/usr/lib/python2.5/xml/parsers/expat.pyc
/usr/lib/python2.5/xml/parsers/expat.py
/usr/lib/libexpat.so.1
root@john-laptop:/home/john# 
==
I create a symlink libexpat.so.1 libexpat.so.0

but still get the same error message

thanks

---

### Post by ibutho on 2008-06-06
Try
```
sudo ln -s /usr/lib/libexpat.so.1.5.2 /usr/lib/libexpat.so
sudo ln -s /usr/lib/libexpat.so.1.5.2 /usr/lib/libexpat.so.1
sudo ldconfig

```

---

### Post by Pawlicki on 2008-06-06
Thanks for your help I did as you suggested but same error message. I know it leaves me scratching my head because your suggestion should do the trick. But not

---

### Post by alexalecu on 2008-07-08
this trick seems to work:
```
sudo ln -s /usr/lib/libexpat.so.1.5.2 /usr/lib/libexpat.so.0
```
(after installing libexpat1)

---

