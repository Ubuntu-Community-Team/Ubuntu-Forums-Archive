---
title: "Using import command in puTTY"
date: 2015-12-18
forum: General Help
---

### Post by Mohsen_Majnoon on 2015-12-18
Hi,

I'm pretty new to Linux world and am struggling with a project with BBB (Beaglebone Black, I'm sure you all know it ;-) ), I'm pretty slow on the learning curve but it's getting better. Since it's Debian, puTTY is my Terminal in Windows, but now that I need to import a library, it can't understand "import" since it's a Python command and I have to use the shebang line. But how can I use it in puTTY? Using [COLOR=#000000][FONT=Ubuntu Mono]#!/usr/bin/python[/FONT][/COLOR]
 before the command in terminal doesn't work apparently right? and when I just type

[LIST]
[*][COLOR=#CC99CC]import[/COLOR][COLOR=#6699CC]Adafruit_BBIO[/COLOR][COLOR=#CCCCCC].[/COLOR][COLOR=#CCCCCC]GPIO [/COLOR][COLOR=#CC99CC]as[/COLOR][COLOR=#CCCCCC] GPIO[/COLOR]
[/LIST]

it just says
 -bash: import: command not found

Any ideas? Thanks in advance.
Mohsen

---

### Post by Mohsen_Majnoon on 2015-12-18
[https://learn.adafruit.com/setting-up-io-python-library-on-beaglebone-black/using-the-bbio-library](https://learn.adafruit.com/setting-up-io-python-library-on-beaglebone-black/using-the-bbio-library)
I'm trying to do this. And I have already passed this step:
[https://learn.adafruit.com/setting-up-io-python-library-on-beaglebone-black/installation-on-ubuntu](https://learn.adafruit.com/setting-up-io-python-library-on-beaglebone-black/installation-on-ubuntu)

---

### Post by Mohsen_Majnoon on 2015-12-18
debian@beaglebone:~$ ls -al
total 44
drwxr-xr-x 4 debian debian 4096 Dec 19 03:28 .
drwxr-xr-x 3 root   root   4096 Nov 12 21:12 ..
drwx------ 3 root   root   4096 Nov 12 21:14 .BBIOServer
-rw-r--r-- 1 debian debian  220 Nov 12  2014 .bash_logout
-rw-r--r-- 1 debian debian 3515 Nov 12  2014 .bashrc
-rw------- 1 root   root      7 Nov 12 21:18 .gitconfig
-rw------- 1    110    116  113 Nov 12 21:15 .npmrc
-rw------- 1 debian debian  186 Nov 12 21:12 .pastebinit.xml
-rw-r--r-- 1 debian debian  675 Nov 12  2014 .profile
-rw------- 1 debian debian   64 Nov 12 21:12 .xsessionrc
drwx------ 2 debian debian 4096 Nov 12 21:12 bin

---

### Post by blm-ubunet on 2015-12-18
Paste this into putty (terminal):
```
sudo python -c "import Adafruit_BBIO.GPIO as GPIO; print GPIO"
```

That code snippet is just to test the python library.
You could stick it into a file.

The shebang is used to "tag" the file. If permissions are set for execute then you don't need to use prefix python/sh/bash etc..

---

### Post by Mohsen_Majnoon on 2015-12-19
Thank you blm-ubunet.

I found if I use the command
```
python
```
then I can use python commands. I apparently didn't read well. Here's though another problem. If I enter python like this I still get errors as it can't use the import command
```
debian@beaglebone:~$ pythonPython 2.7.9 (default, Mar  1 2015, 13:48:22)
[GCC 4.9.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import Adafruit_BBIO.GPIO as GPIO
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named Adafruit_BBIO.GPIO
```

but using it in the format you suggest (and the tutorial suggests as well) it works. So does it mean that whenever I want to use import I should do it this way or is there a work around? Apparently if I instead of ```
python
``` use ```
sudo python
``` I can stay in python and import whatever I want. Is it the way? I know I sound too newb and I have no shame to admit it :D

---

