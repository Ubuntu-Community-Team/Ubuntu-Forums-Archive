---
title: "Targz without configure"
date: 2013-03-18
forum: General Help
---

### Post by tempester on 2013-03-18
Hello. I am rather new to Linux, and I have a problem with installing a tar.gz fie.
I've always had problems installing these types of files, but now I desperately need this program, so I need this problem solved.
on this website [https://code.google.com/p/opentumblr/downloads/list](https://code.google.com/p/opentumblr/downloads/list) i found a program that manages multiple tumblr accounts. I want to install it, but my tar.gz file does not have a configure file.
I saw on forums that you need to run three commands to install a tarball:
./configure
make
make install

none of these work. my file contains only:
AUTHORS
INSTALL
LICENSE
README
setup.py
THANKS
uninstall.sh
opentumblr-qt.desktop

and two folders named "images" and "opentumblrqt"


Install file contains:
INSTALLATION STEPS


* LINUX
    #easy_install simplejson
    #easy_install poster
    #tar -zxvf opentumblr-qt-version.tar.gz
    #cd opentumblr-qt-version
    #python setup.py install
 
Run OpenTumblr
    $opentumblr-qt-client.py


README file contains:
OpenTumblr-Qt
    Tumblr client based on Opentumblr  
 
REQUIREMENTS
    poster ( [http://pypi.python.org/pypi/poster/0.4](http://pypi.python.org/pypi/poster/0.4) )
    simplejson ( [http://code.google.com/p/simplejson/](http://code.google.com/p/simplejson/) )
    python-qt4 ( PyQt4 )
    python
 
DEVELOPERS
    Alejandro Villanueva a.k.a iAlex
    Jair Gaxiola a.k.a jyr


BLOG
    [http://blog.opentumblr.com](http://blog.opentumblr.com)


IRC    
    irc.freenode.net (#opentumblr)



someone please help me, i really need this program installed

---

### Post by steeldriver on 2013-03-18
Hello and welcome

The *configure / make / make install* steps only apply to source code tar packages

EDIT: see schragge's post below - best option is always to instal from standard repos if possible

---

### Post by schragge on 2013-03-18
As *simplejson* and *poster* are in the official repositories, instead of *easy_install*'ing them, try
```
sudo apt-get install python-{qt4,simplejson,poster}
``` If the versions from the Ubuntu repository don't work, you will need to *easy_install* newer versions from [PyPI](https://pypi.python.org/pypi). In order to do that, install *python-setuptools* first: ```
sudo apt-get install python-setuptools
```

---

