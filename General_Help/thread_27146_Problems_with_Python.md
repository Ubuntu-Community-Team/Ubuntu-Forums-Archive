---
title: "Problems with Python"
date: 2005-04-15
forum: General Help
---

### Post by jmather on 2005-04-15
After upgrading to hoary I can not get rid of this error when running apt...

Preconfiguring packages ...
(Reading database ... 97851 files and directories currently installed.)
Unpacking python2.4-pythoncard (from .../python2.4-pythoncard_0.8.1-1ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python2.4-pythoncard_0.8.1-1ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/pythoncard/pythoncard_config.txt', which is also in package python2.3-pythoncard
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4-pythoncard_0.8.1-1ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Has anyone seen this or can tell what to do?
I have tried apt-get -f install....

Thx

---

### Post by Juergen on 2005-04-15
It seems you can't have both 2.3/2.4 packages. I chose to remove the 2.3 one.
For this, go to a command line and
```
dpkg -r python2.3-pythoncard
```dpkg might complain about (for me: 2) dependencies. 
Note them down and 'dpkg -r' them first. The not 2.3-specific you can reinstall afterwards.

---

### Post by jmather on 2005-04-15
That seemed to do it...I had tried using apt-get remove....but that didn't work...had to use dpkg...

Thanks!

I didn't get the dependency warnings...but that probably doesn't mean anything.  After this was done everything seemed to install fine....

---

