---
title: "Removing some unneded packages / cleaning system"
date: 2013-07-05
forum: General Help
---

### Post by Nikolai D. on 2013-07-05
Hi all,
since i have a dualboot system on an ssd drive, the disk space is kinda limited,
so i want to install something to test,
but before i want to clean up some stuff,
if i run Baobab i see that in /usr/share/doc i have several texlive-.. folders that take some (600MB) space. But i already have uninstalled Texmaker that i had installed earlier. Why have they stayed on a system? How can i remove them by giving a command to properly uninstall them? Anyone?
thx,
Nikolai

---

### Post by ajgreeny on 2013-07-05
Depending on version of ubuntu you need ```
sudo apt-get purge texmaker
``` or in older versions of ubuntu (can't remember when it changed) ```
sudo apt-get remove --purge texmaker
``` one or other of those will remove any remaining configuration files and folders of the application.  You should also probably run [code]sudo apt-get autoremove[/code to remove any packages installed as dependencies of something you have since removed, and therefore no longer needed.

---

### Post by Nikolai D. on 2013-07-06
> **ajgreeny said:**
> Depending on version of ubuntu you need ```
sudo apt-get purge texmaker
``` or in older versions of ubuntu (can't remember when it changed) ```
sudo apt-get remove --purge texmaker
``` one or other of those will remove any remaining configuration files and folders of the application.  You should also probably run [code]sudo apt-get autoremove[/code to remove any packages installed as dependencies of something you have since removed, and therefore no longer needed.

i did the purge but the folders stay

---

### Post by gordintoronto on 2013-07-06
Have you also run this command: sudo apt-get clean

This won't help with the files you mentioned, but it might free up more space.

I use Synaptic to "completely remove" unwanted packages. If you reinstall Texmaker then use Synaptic, it might clean things up.

---

### Post by Cheesehead on 2013-07-06
Use the 'dpkg' command to learn which packages are associated with which files.

To learn the package name from a specific file, use the -S (search) flag
For example, here is how to discover that the file /usr/share/doc/hello is installed by the 'hello' package:
```
me@system:~$ dpkg -S /usr/share/doc/hello
hello: /usr/share/doc/hello
```


The inverse is to see all the files installed by a package, use the -L (list) flag
SInce I plan to uninstall 'hello', let's see everything that package installs:
```
me@system:~$ dpkg -L hello
/.
/usr
/usr/share
/usr/share/info
/usr/share/info/hello.info.gz
/usr/share/doc
/usr/share/doc/hello
/usr/share/doc/hello/NEWS
/usr/share/doc/hello/changelog.Debian.gz
/usr/share/doc/hello/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/hello.1.gz
/usr/bin
/usr/bin/hello
```

---

### Post by ajgreeny on 2013-07-09
> **Nikolai D. said:**
> i did the purge but the folders stay

Which folders in particular?  Nothing in your home will be removed with any of these system commands, only files and folders in the root filesystem.

---

