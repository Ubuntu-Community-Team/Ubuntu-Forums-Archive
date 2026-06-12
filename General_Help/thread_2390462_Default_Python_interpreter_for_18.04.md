---
title: "Default Python interpreter for 18.04"
date: 2018-04-29
forum: General Help
---

### Post by loach on 2018-04-29
This is my first post here so sorry if I have missed any conventions.

I was under the impression that the default Python interpreter for Ubuntu for Bionic Beaver is Python 3. I guessed that it would be the same for Xubuntu but after downloading and installing Xubuntu I found that typing "python" in a terminal window resulted in a Python 2.7 interpreter being opened. I did some googling but couldn't find anything.

Have I done something wrong or is Python 2.7 still the default interpreter for Xubuntu?

Thanks in advance!

---

### Post by thenailedone on 2018-04-29
> **loach said:**
> This is my first post here so sorry if I have missed any conventions.

I was under the impression that the default Python interpreter for Ubuntu for Bionic Beaver is Python 3. I guessed that it would be the same for Xubuntu but after downloading and installing Xubuntu I found that typing "python" in a terminal window resulted in a Python 2.7 interpreter being opened. I did some googling but couldn't find anything.

Have I done something wrong or is Python 2.7 still the default interpreter for Xubuntu?

Thanks in advance!

Run **python3**.

---

### Post by loach on 2018-05-02
Thanks for the reply.

I was hoping that it was now the default interpreter as I thought it was for Ubuntu. This is because when doing a lot of terminal work e.g. developing with Django it saves having to type python3 every time instead of just python. I know that you can set up your install to make python 3 the default but I was wondering if that was now the default interpreter.

---

### Post by techtonik on 2018-09-03
The same here. Maybe because I upgraded my system, but my Beaver's Python is still 2.

```
$ python
Python 2.7.15rc1 (default, Apr 15 2018, 21:51:34) 
[GCC 7.3.0] on linux2

```

The only reference to Python 2 in [18.04 release notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Other_base_system_changes_since_16.04_LTS") is that it is not installed by default. But.. there is still 1.5Gb of dependencies when I try to remove it.

---

### Post by Impavidus on 2018-09-03
It must be because you have some software that still depends on python 2.7. When I try to remove python 2.7 on 18.04, the package manager wants to remove a bunch of other python packages, calibre, gimp, hugin and two texlive packages, none of which are installed by default.

Not sure about gimp, it used to be installed by default on Xubuntu, but not Ubuntu. And from the OP, I think gimp may still be installed by default on Xubuntu, but not Ubuntu, which forces installation of python 2.7 on Xubuntu only.

---

### Post by The Cog on 2018-09-03
[https://www.python.org/dev/peps/pep-0394/](https://www.python.org/dev/peps/pep-0394/)

---

