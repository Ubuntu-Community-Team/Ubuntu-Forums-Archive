---
title: "apt-get broken due to misuse of graphiz-cairo"
date: 2007-01-30
forum: General Help
---

### Post by T*&amp;1p87)v# on 2007-01-30
Hi all,

I have a strange problem, some time ago I was playing with compiz and apparenty some of the packages of that installation are causing me some inconvenience, I am able to use my apt-get for the usual tasks, but I keep getting this error whenever I add or remove any packages from the system. Do u have any idea how to resolve this issue??

ayarov@ubuntun:~$ sudo dpkg --configure -a
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127


ayarov@ubuntun:~$ sudo apt-get remove ksirtet
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsoundtouch1c2 mffm-fftw1c2 ksirtet
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ksirtet
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 762kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131603 files and directories currently installed.)
Removing ksirtet ...
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)


ayarov@ubuntun:~$ sudo apt-get remove graphviz-cairo
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsoundtouch1c2 mffm-fftw1c2 graphviz-cairo
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  graphviz-cairo
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 193kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131554 files and directories currently installed.)
Removing graphviz-cairo ...
/var/lib/dpkg/info/graphviz-cairo.postrm: 11: dot: not found
dpkg: error processing graphviz-cairo (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by hatdragon on 2007-02-21
I think the easiest way is simply:

sudo rm /var/lib/dpkg/info/graphviz-cairo.post*
sudo aptitude remove -f graphviz-cairo

I think there's a problem with the graphiz-cairo installation script, and it looks for files that don't exist. The problem has shown up before on this forum:
[http://ubuntuforums.org/showthread.php?p=2117662](http://ubuntuforums.org/showthread.php?p=2117662)
[http://www.ubuntuforums.org/showthread.php?t=365719](http://www.ubuntuforums.org/showthread.php?t=365719)

I think this ought to be an easy fix, but there doesn't appear to be a bug report filed...hmm, I think I'll go do that now.

---

### Post by T*&amp;1p87)v# on 2007-02-21
Great!!!
thanks a million for the fix, I do not get that annoying message any more :)

---

### Post by i8bugs on 2007-02-28
I tried to install graphviz-cairo and there seems to be something wrong with the package and it does not install correctly, leaving you with broken packages.  THEN, you get the broken packages messages when you try do do an ubuntu update package.  Searching the forum led me to this thread (after trying several other commands) and this is the only one that worked.

So the issue is:
1.  The graphviz-cairo package needs removed off of synaptic, or repaired and
2.  People get broken package issues all the time.  We need a program that can diagnose the issue and repair the problem either atomically (I will never remember all those terminal commands...) or provide me with option 1, 2 or 3.

In the world of programming, I wouldn't think this would be too difficult, but I'm not a programmer.

ANYWAY...Thanks for the repair script
i8bugs

---

