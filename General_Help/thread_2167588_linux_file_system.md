---
title: "linux file system"
date: 2013-08-14
forum: General Help
---

### Post by mikel2 on 2013-08-14
hey. i moved to ubuntu not along time ago and i cant understand the file system in windows i know .exe is a execution program dll = dynamic library layers 
and so on.. but it seems i know nothing about ubuntu file system or how exactly this OS run.. i would appreciate every explanation of linux file system and
architecture

---

### Post by mastablasta on 2013-08-14
have a look at community made manual (my signature) or online documentation.

but in short eveything is a file in linux. and if you flag the file as executable you can execute it. so somethign ending in .blahblah can be executed as long as it's compatible with linux and flagged as executable.

---

### Post by Frogs Hair on 2013-08-14
There are plenty of links like this.  :wink:   [http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html](http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html)

---

### Post by TheFu on 2013-08-14
Extensions don't matter on Linux unless a specific program makes them matter. Usually it is only a convenience for people with warped minds ... you know - former MS-Windows users. ;)

**Any** file can become executable on Linux file systems. That is part of the permissions attached to every file.
This [https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) will explain more.  A low level of knowledge about file and directory permissions on UNIX/Linux will help you understand almost everything about UNIX/Linux system permissions.  For example, we can make files executable only be 1 person, a specific group of people or everyone accept a group or specific group of people.  Of course, making a file executable by everyone or nobody is also possible.

The comment from @mastablasta that everything is a file is almost true and a great place to start to understand Linux. Devices are files, mice, keyboards, video, networking, hard drives .... plus directories, and ... er ... files - all of these things are files.  If that is the case, you can understand why learning about file permissions on Linux is a cornerstone skill.

It is also why people like me avoid using GUI programs - those tools tend to hide important file permission data, which we think is critical.  That is very important on multi-user operating systems like Linux.  Just because you are the only user, doesn't mean that there is only 1 user on your machine. I bet there are at least 10-20 users on your machine.

---

### Post by oldos2er on 2013-08-14
> **mikel2 said:**
> hey. i moved to ubuntu not along time ago and i cant understand the file system in windows

I can't understand Windows' file system either, which is yet another reason I use Linux.  :)

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

