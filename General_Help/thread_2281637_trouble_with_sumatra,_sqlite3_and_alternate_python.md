---
title: "trouble with sumatra, sqlite3 and alternate python installation"
date: 2015-06-08
forum: General Help
---

### Post by wizrddreams on 2015-06-08
Hi, there. 
I am currently learning Python and have been working on setting up things away from the system python. 
I am beginning to think I should just switch over the using system python and virtual environments. 
Nevertheless, I have found it very informative following an alternate directory structure and python installation from a textbook. (Python Scripting for Computational Science).

I have run into an issue setting up a book-keeping program called Sumatra. ([https://pythonhosted.org/Sumatra/installation.html](https://pythonhosted.org/Sumatra/installation.html))
It has a few dependencies which I have installed. 
Sumatra works a bit like git for those who don't know of it.
Much like git and using git init, there is a command for Sumatra called smt init. 
However when I go to set-up a directory with smt init I am getting some errors:
```

smt init

Traceback (most recent call last):
  File "/home/directory/ext/Linux/bin/smt", line 5, in <module>
    pkg_resources.run_script('Sumatra==0.6.0', 'smt')
  File "/home/directory/ext/Linux/lib/python2.7/site-packages/distribute-0.6.28-py2.7.egg/pkg_resources.py", line 499, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/home/directory/ext/Linux/lib/python2.7/site-packages/distribute-0.6.28-py2.7.egg/pkg_resources.py", line 1239, in run_script
    execfile(script_filename, namespace, namespace)
  File "/home/directory/ext/Linux/lib/python2.7/site-packages/Sumatra-0.6.0-py2.7.egg/EGG-INFO/scripts/smt", line 7, in <module>
    from sumatra import commands, __version__
  File "/home/directory/ext/Linux/lib/python2.7/site-packages/Sumatra-0.6.0-py2.7.egg/sumatra/commands.py", line 22, in <module>
    from sumatra.projects import Project, load_project
  File "/home/directory/ext/Linux/lib/python2.7/site-packages/Sumatra-0.6.0-py2.7.egg/sumatra/projects.py", line 34, in <module>
    import sqlite3
  File "/home/directory/ext/Linux/lib/python2.7/sqlite3/__init__.py", line 24, in <module>
    from dbapi2 import *
  File "/home/directory/ext/Linux/lib/python2.7/sqlite3/dbapi2.py", line 28, in <module>
    from _sqlite3 import *
ImportError: No module named _sqlite3

```

So I thought I should test importing the module within Python itself. 
I have the system python installed at '/usr/bin/python'
I have another python installed which is active in the terminal at '/home/directory/ext/Linux/bin/python'

System python correctly imports sqlite3, as it should.
Whereas the custom install does not:
```

python
Python 2.7.10 (default, May 28 2015, 12:19:50) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sqlite3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/directory/ext/Linux/lib/python2.7/sqlite3/__init__.py", line 24, in <module>
    from dbapi2 import *
  File "/home/directory/ext/Linux/lib/python2.7/sqlite3/dbapi2.py", line 28, in <module>
    from _sqlite3 import *
ImportError: No module named _sqlite3

```

I came across related posts on stack-overflow. With numerous solutions, none of which have worked for me. 

One solution was to install libsqlite3-dev from the repositories and then re-compile your Python installation. ([http://stackoverflow.com/questions/233320/cannot-import-sqlite-with-python-2-6](http://stackoverflow.com/questions/233320/cannot-import-sqlite-with-python-2-6)) Which I tried and could not get to work. 

The next thing I tried following the post above was to look for the location of the .so files mentioned above. 
So that I could add them to the alternate Pythons PYTHONPATH
So what I did was look for them in the system Python, because sqlite3 and _sqlite3 import without error there.
I searched for the .so (shared object) doing:
```

/usr/bin/python

Python 2.7.6 (default, Mar 22 2014, 22:59:56) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sqlite3
>>> sqlite3.__file__
'/usr/lib/python2.7/sqlite3/__init__.pyc'
>>> import _sqlite
>>> _sqlite.__file__
'/usr/lib/python2.7/dist-packages/_sqlite.so'

```

I then added those directories to my alternative python:
```

python

Python 2.7.10 (default, May 28 2015, 12:19:50) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.path.append('/usr/lib/python2.7/sqlite3')
>>> sys.path.append('/usr/lib/python2.7/dist-packages')
>>> import sqlite3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/directory/ext/Linux/lib/python2.7/sqlite3/__init__.py", line 24, in <module>
    from dbapi2 import *
  File "/home/directory/ext/Linux/lib/python2.7/sqlite3/dbapi2.py", line 28, in <module>
    from _sqlite3 import *
ImportError: No module named _sqlite3

```

Clearly then adding these to the pythonpath does not help in this situation. 

I am really hoping that someone can offer some guidance on how to further work through this. 
I am really not to sure where to go from here. 
I realize that I could switch over to using the system python again, but I have already done so much to get the alternate working. 
I am also stubborn and want it to work on my installation of Python. 
Any advice will be appreciated. 
Thanks!

---

### Post by wizrddreams on 2015-06-11
Hello, again. 
Turns out I was able to get one of the aforementioned solutions to work. 
Namely installing libsqlite3-dev from the Ubuntu repositories, then re-compiling/installing python. 
I believe the first time I re-compiled python I set an option that may have done so incorrectly. 

To recapitulate the problem in concise way. 
I have a non-system python that is installed with a particular directory structure.
Typically system python has libraries like sqlite3 and bz2 for example pre-installed.
A downloaded version of Python (2.7.10) can have problems linking to those libraries.
Hence I was getting ImportErrors like ImportError: No module named _sqlite3 or No module named bz2.

I do not understand why system python can load libraries like sqlite3 and bz2.
Whereas my custom install of python could not.
But I do know that installing the libfoo-dev libraries from the repositories then re-compiling custom Python allowed me to import said libraries. 

To re-compile Python:
```

cd /path-to-python/python/Python-2.7.10
./configure 
make 
make install 
make clean

```

In my case I was trying to use Sumatra (sqlite3 error) and node.js (bz2 error)

Let me know if any of this is incorrect or comment with more information!

---

