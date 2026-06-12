---
title: "Python on 16.04?"
date: 2018-06-02
forum: General Help
---

### Post by andysharpie on 2018-06-02
So, I'm going to start programming (trying to, rather) and I can't figure out if Python is already installed on Ubuntu 16 or not. Searching my file system yields a lot of python-titled results, but I can't even find if I have a working python shell or not. Can anyone help?
-Andy

---

### Post by deadflowr on 2018-06-02
Yes, it's a default package.
Should be python 3.5.
Or something like that.

---

### Post by Impavidus on 2018-06-02
Many vital components of Ubuntu depend on python, so, yes, it's installed by default.

Ubuntu 16.04 comes with 2 versions of python, 3.5 and 2.7, because some components of the OS hadn't been ported yet from python 2 to python 3. The default is 2.7, because the software that depends on python 2 doesn't say so explicitly, where the software that depends on python 3 does say so. Calling python3 should give you python 3.5, if you need that.

You can search the package manager for many python libraries that are not installed by default.
[https://packages.ubuntu.com/xenial/python/](https://packages.ubuntu.com/xenial/python/)

---

### Post by The Cog on 2018-06-02
16.04 comes with both python2 and python3, and the command **python** by default launches python2. Just open a terminal console and enter the command **python** (or **python3**) and you will be presented with a >>> prompt. Most tutorials start off by typing commands at this prompt.
Here is a small screen-scrape from my command prompt (I've put my typing in bold blue):
```
steve@Steves-PC:~$ **[COLOR="#0000CD"]python[/COLOR]**
Python 2.7.15rc1 (default, Apr 15 2018, 21:51:34) 
[GCC 7.3.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> **[COLOR="#0000CD"]a = 55[/COLOR]**
>>> **[COLOR="#0000CD"]b = 99[/COLOR]**
>>> **[COLOR="#0000CD"]print a + b[/COLOR]**
154

```
Pretty soon you will want to use a text editor to save your work in files. gedit is fine but there are lots of alternatives too if you prefer to try others.

---

### Post by monkeybrain20122 on 2018-06-02
I use system pythons as the bare system (I use python3.5) without adding anything else from the repo. I install additional packages with pip (I use get-pip.py instead of sudo apt install python3-pip which is outdated) and compiling. Another option is anaconda.

If you just start, you should focus on python3. python2.7 is still around only because a lot of old codes are written in it, all new codes should be written in python3

---

### Post by andysharpie on 2018-06-02
Thanks a million! I did manage to find it and launch it.
Hasta luego.
-Andy

---

