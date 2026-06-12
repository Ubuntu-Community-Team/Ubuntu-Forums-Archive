---
title: "Package python-tk has no installation candidate"
date: 2008-01-01
forum: General Help
---

### Post by riley468 on 2008-01-01
I am using Python 2.5.1 (r251:54863, Oct 5 2007, 13:36:32) on
Ubuntu 7.10 (Gutsy Gibbon) and have tried to import Tkinter at the Python prompt:

>>> import Tkinter

with the following result:

ImportError: No module named _tkinter, please install the python-tk package.

I tried the following code at the shell prompt:

sudo apt-get install python-tk

with the following result:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package python-tk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
python2.5
E: Package python-tk has no installation candidate

I then googled python-tk and found a possible package here:

[http://packages.ubuntu.com/gutsy/python/python-tk](http://packages.ubuntu.com/gutsy/python/python-tk)

You have searched for the contents of python-tk in gutsy, architecture i386.
Package contains 6 files, displaying files 1 to 6.

FILE                                                       PACKAGE

usr/lib/python2.4/lib-dynload/_tkinter.so		    python/python-tk
usr/lib/python2.5/lib-dynload/_tkinter.so		    python/python-tk
usr/share/doc/python-tk/README.Debian			    python/python-tk
usr/share/doc/python-tk/README.Tk			    python/python-tk
usr/share/doc/python-tk/changelog.Debian.gz		    python/python-tk
usr/share/doc/python-tk/copyright			    python/python-tk

However, when I try to instal using the package installer, I get the following error:

Package python-tk:  Error; Dependency is not satisfiable: blt 

The included files listed are:

./
usr/
usr/lib/
usr/lib/python2.4/
usr/lib/python2.4/lib-dynload/
usr/lib/python2.4/lib-dynload/_tkinter.so
usr/lib/python2.5/
usr/lib/python2.5/lib-dynload/
usr/lib/python2.5/lib-dynload/_tkinter.so
usr/share/
usr/share/doc/
usr/share/doc/python-tk/
usr/share/doc/python-tk/README.Tk
usr/share/doc/python-tk/README.Debian
usr/share/doc/python-tk/copyright
usr/share/doc/python-tk/changelog.Debian.gz

What am I doing wrong? Can anyone help?

Thanks in advance...and a happy new year to all.

---

### Post by taurus on 2008-01-01
Look in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure you have a check mark on all th repos except the last one, Source code and the CDROM at the bottom window.  If you need to add them in, then you must press the Refresh button.  Now, see if you can find that package again in synaptic with the Search option.

---

### Post by Perfect Storm on 2008-01-01
How's your source list looks like? Sounds like it's not set up correctly or interfiring of an un-official source.

---

### Post by riley468 on 2008-01-01
Taurus: I followed your instruction to the letter, and I am happy to report that I was able to import the python-tk module. 

Now when I enter: import Tkinter at the python prompt, I no longer get an error message.

Thank you very much for your rapid response, and I wish you all the best in the new year.

Thank you also to the other responders who responded to my request. I truly appreciate all of your help.

---

