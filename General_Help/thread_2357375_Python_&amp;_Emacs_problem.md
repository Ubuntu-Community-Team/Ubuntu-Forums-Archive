---
title: "Python &amp; Emacs problem"
date: 2017-04-01
forum: General Help
---

### Post by skippylou on 2017-04-01
Using Ubuntu 16.04LTS.  The last time I did any modifications or installing was about a week ago, I installed Emacs GNU Emacs 25.1.1, SBCL and Slime and they all seem to be working fine.  I wanted to try out Python, so:

```
skippy@skippy:~$ sudo apt install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version (2.7.11-1).
python set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up emacs24 (24.5+1-6ubuntu1) ...
Install cmake-data for emacs24
install/cmake-data: Byte-compiling for emacs24
ln: failed to create symbolic link '/usr/share/emacs24/site-lisp/cmake-data/cmake-mode.el': File exists
Warning: arch-dependent data dir `/usr/lib/emacs/24.5/x86_64-linux-gnu/': No such file or directory
Warning: Lisp directory `/usr/share/emacs/24.5/lisp': No such file or directory
Error: charsets directory not found:
/usr/share/emacs/24.5/etc/charsets
Emacs will not function correctly without the character map files.
Please check your installation!
Install emacsen-common for emacs24
emacsen-common: Handling install of emacsen flavor emacs24
Warning: arch-dependent data dir `/usr/lib/emacs/24.5/x86_64-linux-gnu/': No such file or directory
Warning: Lisp directory `/usr/share/emacs/24.5/lisp': No such file or directory
Error: charsets directory not found:
/usr/share/emacs/24.5/etc/charsets
Emacs will not function correctly without the character map files.
Please check your installation!
ERROR: install script from emacsen-common package failed
dpkg: error processing package emacs24 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs24
E: Sub-process /usr/bin/dpkg returned an error code (1)
skippy@skippy:~$
```

I don't know where to begin and am confused by all the error references to Emacs 24.5 and emacs24.  Apparently I should try installing or re-installing something, but what?

Thanks for any help.

---

### Post by Futant on 2017-04-02
Hi, try reinstalling [this way](http://ubuntuhandbook.org/index.php/2016/09/install-gnu-emacs-25-1-in-ubuntu-16-04/).

If you're just starting out in Python you might also want to consider using [Python 3 rather than 2]("https://wiki.python.org/moin/Python2orPython3").

Also, please use code tags when posting terminal activity :)

---

### Post by skippylou on 2017-04-03
Basically the same story:

```
skippy@skippy:~$ sudo apt install build-essential checkinstall
[sudo] password for skippy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
checkinstall is already the newest version (1.6.2-4ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up emacs24 (24.5+1-6ubuntu1) ...
Install emacsen-common for emacs24
emacsen-common: Handling install of emacsen flavor emacs24
Warning: arch-dependent data dir `/usr/lib/emacs/24.5/x86_64-linux-gnu/': No such file or directory
Warning: Lisp directory `/usr/share/emacs/24.5/lisp': No such file or directory
Error: charsets directory not found:
/usr/share/emacs/24.5/etc/charsets
Emacs will not function correctly without the character map files.
Please check your installation!
ERROR: install script from emacsen-common package failed
dpkg: error processing package emacs24 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs24
E: Sub-process /usr/bin/dpkg returned an error code (1)
skippy@skippy:~$
```

---

### Post by Richard_Romick on 2017-04-04
caveat: most of my experience working with python is in Debian

Do you have python 3 installed?

try running
"python3 -V"
and see if it gives you a python3 version number.

It seems that when you try installing python2.7 (referenced when you try installing "python") it depends on files from emacs24, which it can no longer find due to your emacs25.1 installation.  This can be an issue when installing the new software ahead of the current OS repository release.

To be absolutely clear, when you use python in the terminal:
"python" is python2.7
"python3" is python3

---

### Post by steeldriver on 2017-04-04
How exactly did you install Emacs GNU Emacs 25.1.1? you issues seem to be related to an incomplete / conflicting installation of emacs - and nothing to do with python

Both python (aka python2) and python3 should be installed in any recent base Ubuntu distribution - trying to install any version other than the standard version from the repository most often ends in tears

---

