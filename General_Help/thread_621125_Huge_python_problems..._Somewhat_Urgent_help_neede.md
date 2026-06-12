---
title: "Huge python problems... Somewhat Urgent help needed :("
date: 2007-11-23
forum: General Help
---

### Post by Crushyerbones on 2007-11-23
I'm having these strange problems with python. First every program with an input in it would crash the assembler and the program itself as soon as the "enter key" was pressed. Now I found out I can't even launch PyPE and use the python shell in DrPython!

I have an assignment due on Tuesday which requires python... I really don't want to have a reason to install XP on my laptop again...  I've even tried reinstalling Ubuntu :(  (Not a fresh reinstall, just removed python and installed everything else).

I would be very helpful for any help at all, even debugging.

---

### Post by kaffe_02 on 2007-11-23
Have you checked which version of python your using?  Have you tried your code on another computer?  Are you getting any errors?

---

### Post by Crushyerbones on 2007-11-23
Yes, it works fine. Infact, having the python shell crash with an empty document was a dead giveway it wasn't my code.

Last friday there was also a joke going around my campus that I single-handedly created a 1 line piece of code which would kill whatever compiled it outright :p  ( it was a=input()   )

The file I'm using to test this is exactly:
a=raw_input()

print a


Terminal Compiles it just fine, it's just DrPython and SPE that crash as soon as I press enter (altough SPE doesn't quit, it just says the script has finished).


I've tried 2.5 and 2.4 but it doesn't make any difference at all. I think DrPython used to invoke 2.4 on it's shell.



By the way, if I take a screenshot just at the right time, I can see Drpython prints this out in the place the shell should be, just before crashing:
/usr/bin/python -u -i
Also, regardeless of I use the shell to crash it or just use a simple input(), running Drpython in the terminal shows me a "Segmentation fault (core dumped)"

---

### Post by Crushyerbones on 2007-11-23
Anyone have any tips? Please?

---

### Post by LaRoza on 2007-11-23
Use raw_input()

[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

---

### Post by Crushyerbones on 2007-11-23
> **LaRoza said:**
> Use raw_input()

[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

I don't think anyone understands my problem :p

---

### Post by Martin Witte on 2007-11-23
to get more help i suggest you give some more details, eg

is your problem only that drpython and pype crash?
did you run the pythonscript already from a terminal?
does idle crash as well?
what versions are using, where did you get drpython and pype?
what os and what version of that os are you on?

---

### Post by Crushyerbones on 2007-11-23
> **Martin Witte said:**
> to get more help i suggest you give some more details, eg

is your problem only that drpython and pype crash?
**No, my problem is that so far I can't compile anything if it has an input() or raw_input() command in it in anything else besides the terminal. I also can't use the python shell in DrPython. PyPE won't even launch.**


did you run the pythonscript already from a terminal?
**What's pythonscript? You mean the program? Yes, it runs fine on the terminal, which is strange**

does idle crash as well?
**Just installed it. Yes it does work fine from what I've tested**

what versions are using, where did you get drpython and pype?
**Drpython: 165. Pype: 2.5-2. Synaptic.**

what os and what version of that os are you on?
**Ubuntu 7.10**


Another thing, here's my PyPE console output:
```
/usr/share/pype/pype.py:38: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import *
[ Fri Nov 23 21:09:04 2007 ] Loading menus from /home/pedro/.pype/menus.txt
Loading history from /home/pedro/.pype/history.txt
[ Fri Nov 23 21:09:05 2007 ] Traceback (most recent call last):
  File "/usr/bin/pype", line 7, in <module>
    pype.main()
  File "/usr/share/pype/pype.py", line 4350, in main
    filehistory.root = root = app.frame = MainWindow(None, -1, "PyPE", docs)
  File "/usr/share/pype/pype.py", line 676, in __init__
    menuAddM(menuBar, filemenu, "&File")
  File "/usr/share/pype/pype.py", line 248, in menuAddM
    if isinstance(parent, wxMenu) or isinstance(parent, wxMenuPtr):
NameError: global name 'wxMenuPtr' is not defined
```

---

### Post by Martin Witte on 2007-11-24
looks like pype has a bug. i suggest to choose another ide, se eg. [http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments) for some ideas. i'm using idle, thats great for me.

---

### Post by Crushyerbones on 2007-11-24
I really hate bumping myself but this driving me nuts... :S I'll wait about 3 more hours before going back to XP...

Edit: I only saw that reply just now xD

Does anyone know any way to for DrPython to use python2.4?

---

### Post by Martin Witte on 2007-11-24
why don't you use python 2.5.1, this comes standard with ubuntu 7.10, and is probably compatible with drpython 165 in the repositories

---

### Post by Crushyerbones on 2007-11-24
You're right... I've tried running Drpyhon on 2.4 but it didn't change anything... 

Let's think this over carefully... Dr.python crashes when using inputs or using the shell. Terminal works fine. What could cause that?

---

### Post by Crushyerbones on 2007-11-24
I don't think this is supposed to happen?

```
pedro@pcaetano:~$ sudo apt-get install idle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.4-minimal
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-tk
Suggested packages:
  tix
The following NEW packages will be installed:
  idle python-tk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 45.2kB of archives.
After unpacking 233kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main python-tk 2.5.1-1ubuntu1 [42.1kB]
Get:2 http://archive.ubuntu.com gutsy/main idle 2.5.1-1ubuntu2 [3080B]
Fetched 45.2kB in 0s (72.7kB/s)
Selecting previously deselected package python-tk.
(Reading database ... 133580 files and directories currently installed.)
Unpacking python-tk (from .../python-tk_2.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package idle.
Unpacking idle (from .../idle_2.5.1-1ubuntu2_all.deb) ...
Setting up bicyclerepair (0.9-4.1ubuntu2) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
pycentral: pycentral pkginstall: error byte-compiling files (78)
pycentral pkginstall: error byte-compiling files (78)
dpkg: error processing bicyclerepair (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-setuptools (0.6c6-1) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
pycentral: pycentral pkginstall: error byte-compiling files (45)
pycentral pkginstall: error byte-compiling files (45)
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-kiwi:
 python-kiwi depends on python-setuptools (>= 0.6b3-1); however:
  Package python-setuptools is not configured yet.
dpkg: error processing python-kiwi (--configure):
 dependency problems - leaving unconfigured
Setting up python-profiler (2.5.1-1ubuntu1) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
pycentral: pycentral pkginstall: error byte-compiling files (2)
pycentral pkginstall: error byte-compiling files (2)
dpkg: error processing python-profiler (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-tk (2.5.1-1ubuntu1) ...
Setting up idle (2.5.1-1ubuntu2) ...

Errors were encountered while processing:
 bicyclerepair
 python-setuptools
 python-kiwi
 python-profiler
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Martin Witte on 2007-11-24
it looks to me that your ubuntu is a bit screwed, as i believe that the package management system apt-get/dpkg system uses python under the hood. did you remove python 2.5.1 and installed python 2.4.x? if so please re-install python 2.5.1

---

### Post by Crushyerbones on 2007-11-24
Screwing around just isn't taking me anywhere...

Yeah, nevermind... Just fixed it... Turns out changing the python 2.5 shortcut with a 2.4 one wasn't such a great idea. Anyway I'm going to reinstall ubuntu... I don't want to go back to the clutches of miscrosofty hell. :lolflag:


Wish me luck :mad:

---

### Post by Martin Witte on 2007-11-25
glad its solved. good luck!

---

