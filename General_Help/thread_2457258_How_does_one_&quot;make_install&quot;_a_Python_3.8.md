---
title: "How does one &quot;make install&quot; a Python 3.8 source package?"
date: 2021-01-28
forum: General Help
---

### Post by bcschmerker on 2021-01-28
**Having discovered 27 January 2021 that OpenLP at GitLab has declared releases up to 2.4.6-1 a WontFix,** I downloaded OpenLP-2.9.2.tar.gz to /home/webmaster/Downloads on the *e*machines®/ac*e*r® EL1210-09 that I'm preparing for projection duty, extracted the package to /usr/local/src on the rig cited.  I *had* used the GNU Compiler Collection for C+ source before, recognizing Makefiles, Procedures.c, and Headers.h ; but Python is new to me.  I searched for a Makefile in openlp-2.9.2, finding none - only a tree full of Procedures.py.  What Packages would I need for the Python 3.8 install; and how does one go about the make?

---

### Post by TheFu on 2021-01-29
You should use a virtual environment (in Python terms) to load and use any non-system versions of python. DO NOT REPLACE the system pythons.
Most of the virtual environment management tools, like pyenv, will pull the specific version of python for you, compile it from source, and setup the environment so your userid, inside that terminal instance, can make use of it.  There will be instructions on making it default to that version by modifying your ~/.bashrc file as well.

[https://realpython.com/intro-to-pyenv/](https://realpython.com/intro-to-pyenv/) has a longer explanation.

---

### Post by Holger_Gehrke on 2021-01-30
@TheFu: He wants to install openlp, not Python itself; it should run quite well with any python3 newer than 3.6 (default on 18.4 is 3.6.9 so he should have something newer than that on 20.04)

Python is not a traditional compiled language. It can compile to byte code (files with the extension .pyc or .pyo for optimized bytecode) but usually you will just run the .py source through the interpreter / byte code compiler. It's quite normal for a python program not to have a Makefile or anything like that.
If [this]("https://openlp.org") is the openlp you're talking about, than installation is quite simple. Python has its own packaging system with the Python Package Index (pypi.org) as repository and pip or pip3 as the tool to manage packages. openlp is on pypi. A simple 'pip3 install openlp' in a terminal will download the program and its dependencies and install it into $HOME/.local - an installation just for the current user, won't damage any system packages but can only be run in the account it was installed in; a system installation should be just as simple ('sudo pip3 install openlp') and should end up in /usr/local but I haven't tried that and since openlp installs quite a few packages which might conflict with system packages I'm not going to try that. To start the program just enter 'openlp' in a terminal or create a .desktop file for it so you can start it graphically.

Holger

---

### Post by TheFu on 2021-01-30
```
$ python3 --version
Python 3.8.5
```

That's the default version on 20.04, at least I think it is.  I'm not running pyenv on my only 20.04 system.

---

### Post by bcschmerker on 2021-02-02
[@Holger_Gehrke](https://ubuntuforums.org/member.php?u=1961578)  **Complicated, but enough info to start the process.**  I noted that OpenLP 2.9.2 requires PIP to run properly; found the Packages in Synaptic, downloaded and installed.  Dialing up 2.9.2 should require a coded symlink in /usr/local/bin to the Python 3.8 run-time binary in /usr/bin.

---

### Post by Holger_Gehrke on 2021-02-02
> **bcschmerker said:**
>  Dialing up 2.9.2 should require a coded symlink in /usr/local/bin to the Python 3.8 run-time binary in /usr/bin.

No. python2, python3 and python should all be in directories that are in $PATH (actually they should all be in /usr/bin and 'python' should be a symlink to the one of the other two which interprets the default version of the python language for the system; Version 2 and 3 are different from each other in a lot of subtle and not so subtle ways).

The main executable for openlp is a python script that uses a shebang line like '#!/usr/bin/env python3' which makes the system run the script using the python3 interpreter found in $PATH. 

openlp depends on PyQt5 and will probably install a version of that newer than the one in the Ubuntu repositories. This is not a big thing if you install it for one user but if you're using some program from the Ubuntu repositories that is written in Python and uses PyQt5 there might be trouble (Qt is a graphical Toolkit which is used by both the KDE and the LXQT desktop; if you're using either of KUbuntu or LUbuntu then you probably have some programs which might be affected by a newer version of PyQt5). 

Holger

---

