---
title: "Python Invalid Installation"
date: 2005-04-13
forum: General Help
---

### Post by Whiffle on 2005-04-13
Hey-

I'm trying to install FTPCube, because I like it better than Gftp, but when I run

```
python setup.py install
```

 for the setup file I got from the ftpcube website, I get this error:

```
  import wx.lib.floatbar
running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)
``` 

Anybody know where this comes from, or what I can do about it?

---

### Post by Whiffle on 2005-04-13
bumpity bump

---

### Post by Dr Gonzo on 2005-04-13
```
sudo apt-get install python2.4-dev
```Most packages have a <packagename>-dev installation candidate that gives you the header files, etc. needed to build stuff from source.  So, for instance, if you want to build a gtk2 app from source, you will need libgtk2.0-dev installed on your system.

---

### Post by Whiffle on 2005-04-13
[QUOTE=Dr Gonzo]```
sudo apt-get install python2.4-dev
```Most packages have a <packagename>-dev installation candidate that gives you the header files, etc. needed to build stuff from source.  So, for instance, if you want to build a gtk2 app from source, you will need libgtk2.0-dev installed on your system.[/QUOTE]
 Awesome, thanks.  That fixed it.  I figured it was something I needed to install, but when I searched python in synaptic I got about eleventy billion hits and didn't feel like installing all of them... :D

DOH...it installed, won't run though...hmmmm..

---

