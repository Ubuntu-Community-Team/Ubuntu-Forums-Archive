---
title: "Error install wxPython on Ubuntu"
date: 2014-01-28
forum: General Help
---

### Post by Muhammad_Al_Ikhsan on 2014-01-28
Good morning,

I have a problem when install wxpython on my Ubuntu. My ubuntu version is :
```
root@bt:/# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid
root@bt:/# 

```
I got an error in wxPython when i try to apt-get upgrade :
```
root@bt:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  python-wxgtk2.8-dbg: Depends: python-wxgtk2.8 (= 2.8.12.1-0) but 2.8.10.1-0ubuntu1.2 is installed
E: Unmet dependencies. Try using -f.
root@bt:/# 

```


and when i try apt-get -f install show error like this :
```
root@bt:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-wxgtk2.8
Suggested packages:
  python-xml
The following packages will be upgraded:
  python-wxgtk2.8
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/8,500kB of archives.
After this operation, 9,763kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `python-wxgtk2.8-ansi' missing, assuming package has no files currently installed.


dpkg: warning: files list file for package `python-wxgtk2.8' missing, assuming package has no files currently installed.


dpkg: warning: files list file for package `python-wxgtk2.8-dbg' missing, assuming package has no files currently installed.
(Reading database ... 317945 files and directories currently installed.)
Preparing to replace python-wxgtk2.8 2.8.10.1-0ubuntu1.2 (using .../python-wxgtk2.8_2.8.12.1-0_i386.deb) ...
Unpacking replacement python-wxgtk2.8 ...
dpkg: error processing /var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-0_i386.deb (--unpack):
 trying to overwrite '/usr/share/pyshared/wx-2.8-gtk2-unicode/wxversion.py', which is also in package python-wxversion 0:2.8.10.1-0ubuntu1.2
Errors were encountered while processing:
 /var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@bt:/# 

```

Who can help me with this error :( 
Thanks before

---

### Post by jeanjd63 on 2014-01-29
Hello

You can try :
**dpkg  -i  --force-all  **[COLOR=#000000][FONT=Ubuntu Mono]**/var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-0_i386.deb**
then
**apt-get install -f**[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-01-29
lucid has reached end of life 9 months ago and its repositories are closed down. Please save your data and install an up to date version of Ubuntu (12.04 or 13.10) . It has been almost 4 years since lucid's release, all its libraries are ancient, so you shouldn't expect being able to meet the dependencies.

---

### Post by claracc on 2014-01-29
What ubuntu lucid have you installed?, is a desktop release or a server release?.

In order to know, you can run in a xterm, the command:

```
uname -a
```

To see if you are running a desktop (generic) kernel or a server one.

Lucid desktop release has reached its end of life, so you won't be able to  find the repositories in server, but the server release is extended till april 2015

I have just noted you have
```
Description:	Ubuntu 10.04.3 LTS
```
 and the server release extended till 2015 is 10.04.4

---

### Post by deadflowr on 2014-01-29
> **claracc said:**
> What ubuntu lucid have you installed?, is a desktop release or a server release?.


Picture is a desktop version, but seems the OS looks like backtrack.
Hence the root@bt# prompt.

To the OP,  is this backtrack?

---

### Post by Muhammad_Al_Ikhsan on 2014-01-29
> **jeanjd63 said:**
> Hello

You can try :
**dpkg  -i  --force-all  **[COLOR=#000000][FONT=Ubuntu Mono]**/var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-0_i386.deb**
then
**apt-get install -f**[/FONT][/COLOR]
Thanks bro . My problem was fixed :)

```
root@bt:~# dpkg -i --force-all /var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-0_i386.deb
(Reading database ... 
dpkg: warning: files list file for package `python-wxgtk2.8-ansi' missing, assuming package has no files currently installed.


dpkg: warning: files list file for package `python-wxgtk2.8' missing, assuming package has no files currently installed.


dpkg: warning: files list file for package `python-wxgtk2.8-dbg' missing, assuming package has no files currently installed.
(Reading database ... 317945 files and directories currently installed.)
Preparing to replace python-wxgtk2.8 2.8.10.1-0ubuntu1.2 (using .../python-wxgtk2.8_2.8.12.1-0_i386.deb) ...
Unpacking replacement python-wxgtk2.8 ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/pyshared/wx-2.8-gtk2-unicode/wxversion.py', which is also in package python-wxversion 0:2.8.10.1-0ubuntu1.2
Setting up python-wxgtk2.8 (2.8.12.1-0) ...


Processing triggers for python-central ...
root@bt:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-wxgtk2.8-dbg (2.8.12.1-0) ...
root@bt:~# python
Python 2.6.5 (r265:79063, Oct  1 2012, 22:07:21) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> imoprt wx
  File "<stdin>", line 1
    imoprt wx
            ^
SyntaxError: invalid syntax
>>> import wx
>>> 

```

---

### Post by Muhammad_Al_Ikhsan on 2014-01-29
> **monkeybrain20122 said:**
> lucid has reached end of life 9 months ago and its repositories are closed down. Please save your data and install an up to date version of Ubuntu (12.04 or 13.10) . It has been almost 4 years since lucid's release, all its libraries are ancient, so you shouldn't expect being able to meet the dependencies.

Can i update my Bactrak to Ubuntu 13.10? Because i need a backtrack tools to penetration testing, and tools all i need unavailable on ubuntu 13.10 :(

> **claracc said:**
> What ubuntu lucid have you installed?, is a desktop release or a server release?.

In order to know, you can run in a xterm, the command:

```
uname -a
```

To see if you are running a desktop (generic) kernel or a server one.

Lucid desktop release has reached its end of life, so you won't be able to  find the repositories in server, but the server release is extended till april 2015

I have just noted you have
```
Description:    Ubuntu 10.04.3 LTS
```
 and the server release extended till 2015 is 10.04.4

uname -a
```
root@bt:~# uname -a
Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux
root@bt:~#
``` 

Thanks for your help bro :)

---

