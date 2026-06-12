---
title: "Help: Stubborn Python 3.8 Refusing To Be Removed/Uninstalled"
date: 2020-04-26
forum: General Help
---

### Post by ruith on 2020-04-26
UPDATE

Thanks to those who kindly offered ideas on how to resolve the glitch.

I'm happy to report that I found a way to delete the folder/contents via this command in the relevant directory:

[I]sudo rm -rf *

[/I]No doubt a fix known to those veteran Ubuntu lovers, but for those of us setting out and facing a similarly persistent folder, or write protected
give that command a go. It may just do the trick :)

---

### Post by Impavidus on 2020-04-26
Ubuntu 18.04 comes with Python 2.7 and Python 3.6. Both are supported with security upgrades. You need a special reason to install Python 3.8. Various components of Ubuntu rely on Python, so you can't simply replace 3.6 by 3.8. There are some tricks to install them side-by-side.

How did you install Python 3.8? You suggest you downloaded it from somewhere and unpacked it in your home directory. Why is it write protected? It's a bit uncommon to write protect files for the owner. The command **sudo -r /my/locked/directory** wil only remove your locked directory if you actually called it /my/locked/directory, which sounds implausible. That placeholder text must be replaced by the actual directory name.

Apt-get can only remove things that were installed by the package manager. It doesn't know about things you installed in any other way. Pip can handle python packages, but I doubt it can handle stuff you installed manually.

It appears you don't really know what you're doing. You say Python 3.8 is in your Downloads directory. Let's have a look there:```
ls -l ~/Downloads
```Copy-paste the output to the forum. Feel free to skip any lines not related to Python 3.8.

---

### Post by ruith on 2020-04-26
Hi, thanks for your comment. I attempted to install it in order to run a python tool that required 3.8...In followed the commands from -> [https://bongobinary.com/post/install-python38-on-ubuntu](https://bongobinary.com/post/install-python38-on-ubuntu)

I'll be sure to copy/paste the directory contents....back soon

> mzdeet@mzdee:~$ cd Downloads
mzdeet@mzdee:~/Downloads$ ls
Python-3.8.0

[B]and the output is as follows: drwxr-xr-x  4 mzdee mzdee 4096 Apr 26 11:03 Python-3.8.0
[/B]

---

### Post by mcellius on 2020-04-26
I'm running Ubuntu 20.04, and it seems to have Python3.8 already:

```
mdk@jalapano:~$ python3
Python 3.8.2 (default, Mar 13 2020, 10:14:16) 
[GCC 9.3.0] on linux
```

Maybe you just needed to run an update and upgrade?

---

### Post by ruith on 2020-04-26
Hi mcellius..do that each day after powering up the machine..natively my 18.04 has Python 2.7.17 and Python 3.6.9

---

### Post by dragonfly41 on 2020-04-26
Perhaps you would find conda useful (or pyenv) to switch between Python environments. However conda (anaconda) does pile in a very heavy load of packages so I would research that first before jumping in to install.

---

### Post by ruith on 2020-04-26
dragonfly, thanks for the suggestion..and really value your advice on installing..right now I'm focusing on resolving the persistent folder/directory before exploring further

---

### Post by oldfred on 2020-04-26
Note any use of rm command is extremely dangerous. Not for users with limited knowledge.
And rm not the way to uninstall an application and its files.

Also python 3.8 is required for 20.04.

Normally users should not change any python that is default install in Ubuntu as it is required for Ubuntu to work.
Only if you want a newer or older version would you add it normally and then can remove it normally using command line (apt), or synaptic. And that should not be required as python3 default version should run all python3 applications. Only if some old application that needs python2, now obsolete and should not really be used, may you need to install python 2.7.

---

### Post by ruith on 2020-04-26
oldfred, thanks for taking time to comment and offer that helpful advice.

In my case, running 18.04 the 3.8 was not entirely necessary, I'd only tried to install to see if a program would run with it. In that sense it was not the default python. 

the native python on my machine is 2.7.17 and Python 3.6.9.                 

I hear you on using 'rm' but having attempted a number of ways to remove what was a persistent (and failed install) folder I used that removal as a last resort. 

Lessons have been gained for me and I appreciate the suggestions and info offered.

---

