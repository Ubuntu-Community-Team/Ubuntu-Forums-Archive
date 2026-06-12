---
title: "ImportError: cannot import name sessionmaker"
date: 2008-03-25
forum: General Help
---

### Post by medicatedlain on 2008-03-25
This is my first attempt at compiling something.  ...While writing this post, I think I discovered the problem, but I still need help fixing it.  

The read me says: 

Prerequisites:

1. A recent python (2.4 should be fine)
2. libqt4.2+
3. python-qt/pyqt 4.2+
4. sqlalchemy 0.4.1+
5. simplejson 1.7.3+
6: pysqlite2 1.3.0 or python2.5

I tried to install all the prerequisites from synaptic package manager, but looking to make sure I had all the right files, I discovered the only thing available for sqlalchemy was version 0.3.10-1.  How do I get the version I need?

instructions to install:
1. cd; tar xzf ankiqt<...>.tgz
2. cd ankit<...>/libanki
3. sudo python setup.py install
4. cd ..; sudo python setup.py install
5. anki

When I get to step 4 I get error message:

---------------------------------------------------------------------------
This script requires setuptools version 0.6c5 to run (even to display
help).  I will attempt to download it for you (from
[http://cheeseshop.python.org/packages/2.5/s/setuptools/](http://cheeseshop.python.org/packages/2.5/s/setuptools/)), but
you may need to enable firewall access for this script first.
I will start the download in 15 seconds.

(Note: if this machine does not have network access, please obtain the file

   [http://cheeseshop.python.org/packages/2.5/s/setuptools/setuptools-0.6c5-py2.5.egg](http://cheeseshop.python.org/packages/2.5/s/setuptools/setuptools-0.6c5-py2.5.egg)

and place it in this directory before rerunning this script.)
---------------------------------------------------------------------------
Downloading [http://cheeseshop.python.org/packages/2.5/s/setuptools/setuptools-0.6c5-py2.5.egg](http://cheeseshop.python.org/packages/2.5/s/setuptools/setuptools-0.6c5-py2.5.egg)
Traceback (most recent call last):
  File "setup.py", line 6, in <module>
    import anki
  File "/home/lain/Desktop/anki-0.9.5.4/libanki/anki/__init__.py", line 59, in <module>
    from anki.deck import DeckStorage
  File "/home/lain/Desktop/anki-0.9.5.4/libanki/anki/deck.py", line 24, in <module>
    from anki.db import *
  File "/home/lain/Desktop/anki-0.9.5.4/libanki/anki/db.py", line 22, in <module>
    from sqlalchemy.orm import mapper, sessionmaker, relation, backref, \
ImportError: cannot import name sessionmaker

---

