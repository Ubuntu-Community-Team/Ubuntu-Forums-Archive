---
title: "Python Problem?"
date: 2006-10-08
forum: General Help
---

### Post by Mr. Picklesworth on 2006-10-08
Today I noticed 14 updates for my system (Ubuntu Dapper), one of which I am assuming was an update to Python.
Naturally, I chose to install them all without too much worry (though I did check for a kernel update so I know to make sure nothing breaks and I *think* I saw an update to Python).

A little while through, I got an error message saying:
> E:python2.4-minimal: subprocess post-installation script returned error
exit status 1

I believe Python was updated here (especially since python2.4-examples is still in the updates list), but Python itself is no longer in the list of updates (which tells me that it installed correctly).
It appears that 4 updates installed correctly before this happened, so it is very probable that my problem is caused by an update.

Okay, so I think Python was updated and that's about all I know.
Can anyone confirm?

I now have 10 updates that will not install because of that error, and trying to install other packages (eg: An mp3 decoder) also does the same.

Help, please? :)


Edit:
Found this... trying now.
[http://ubuntuforums.org/showthread.php?t=270282&highlight=python+2.4](http://ubuntuforums.org/showthread.php?t=270282&highlight=python+2.4)

Edit:
No go.
I got the following error in the terminal after trying sudo dpkg --configure -a
> Setting up python2.4-minimal (2.4.3-0ubuntu6) ...
Compiling python modules in /usr/lib/python2.4 ...
Compiling /usr/lib/python2.4/site-packages/kuartetlib/ScrollPane.py ...
  File "/usr/lib/python2.4/site-packages/kuartetlib/ScrollPane.py", line 11
    Pane.__init__(self, parent, x, y, size=[0,0], name='', border=0):
                                                                    ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.3-0ubuntu6); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gdbm:
 python2.4-gdbm depends on python2.4 (= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-gdbm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-tk:
 python2.4-tk depends on python2.4 (= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-dev:
 python2.4-dev depends on python2.4 (= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
 python2.4-gdbm
 python2.4-tk
 python2.4-dev


---

### Post by bruce89 on 2006-10-08
There was a update of python2.4 in Dapper earlier - [https://launchpad.net/distros/ubuntu/+source/python2.4](https://launchpad.net/distros/ubuntu/+source/python2.4)

---

### Post by Mr. Picklesworth on 2006-10-08
Righto.

I've updated the parent with an attempted and failed fix which probably reveals some useful information.

---

### Post by halfvolle melk on 2006-10-08
Hi,
Had the same problem yesterday while upgrading. Here's a way to fix it (worked for me anyway).
```
sudo vi /usr/lib/python2.4/site-packages/kuartetlib/ScrollPane.py
```
and change
```
Pane.__init__(self, parent, x, y, size=[0,0], name='', border=0):
```
to
```
Pane.__init__(self, parent, x, y, size=[0,0], name='', border=0);
```
ie : -> ;

---

### Post by Mr. Picklesworth on 2006-10-09
Yay, it works!
Thanks a lot :)

So, is that a typo by the Python folks, a glitch in the updater, or something else?
Swapping a semicolon for a colon seems a bit weird :/

---

### Post by halfvolle melk on 2006-10-09
> **Mr. Picklesworth said:**
> So, is that a typo by the Python folks or a glitch in the updater?
Swapping a semicolon for a colon seems a bit weird :/
I'm not sure, but Python syntax wants a ; at the end. So I think the Kuartet package is broken or something (or maybe not, I'm just a nub :)). But how that can break the upgrade process ... no clue!

---

### Post by Mr. Picklesworth on 2006-10-09
Woohoo!
I got a new error trying to install the Java Runtime Environment.
Forgot to copy it, though... I'll try to reproduce.
For now I believe it may have ended with "exit status 10".

It resulted in a broken package (jre), and now EasyUbuntu (which I was using to get that and some audio codecs) does not start; it gets as far as me entering my admin password, then it disappears.

Additionally, the mp3 codec which I have is broken. I'm not sure if the two problems are related or not.
(Ah, Python is a wonderful thing :/)

---

