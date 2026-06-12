---
title: "Maple 15"
date: 2013-01-19
forum: General Help
---

### Post by carranty on 2013-01-19
I'm trying to install a copy of Maplesoft's Maple 15 onto my home computer.  This is a legal copy, obtained from my university library.  It comes on a CD, which contains an .bin file that installs the software onto my system.  Installation goes fine, but when I run the program I get the following error

```
carranty@Carranty-Desktop:~/maple15$ ./bin/xmaple 
/home/carranty/maple15/bin/maple: 1: eval: /home/carranty/maple15/jre.X86_64_LINUX/bin/java: not found
```I'm running 64bit ubuntu 12.04.  I have java installed 

```
carranty@Carranty-Desktop:~/maple15$ java -version
java version "1.7.0_09"
OpenJDK Runtime Environment (IcedTea7 2.3.3) (7u9-2.3.3-0ubuntu1~12.04.1)
OpenJDK 64-Bit Server VM (build 23.2-b09, mixed mode)

```Here are the contents of the maple15 directory
```
carranty@Carranty-Desktop:~/maple15$ ls
afm                  Install.html                       MapleToolbox_Linux.bin
bin                  java                               readme.txt
bin.IBM_INTEL_LINUX  jre.IBM_INTEL_LINUX                samples
data                 lib                                test
etc                  license                            toolbox
EULA.html            man                                uninstall
examples             Maple_15_InstallLog.log            X11_defaults
examplesclassic      Maple Cloud Terms of Service.html
extern               MapleToolbox
```If I rename the jre.IBM_INTEL_LINUX folder to jre.X86_64_LINUX, maple loads but is "unable to establish a kernel connection" (which means its completely useless).

Going a different route, I thought I'd try linking where it is looking for the java file, to where it actually is

```
carranty@Carranty-Desktop:~/maple15$ locate libjava.so
/home/carranty/maple15/jre.IBM_INTEL_LINUX/lib/i386/libjava.so
/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/libjava.so

carranty@Carranty-Desktop:~/maple15$ ln -s /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/libjava.so jre.X86_64_LINUX/bin/java
carranty@Carranty-Desktop:~/maple15$ ./bin/xmaple 
/home/carranty/maple15/bin/maple: 1: eval: /home/carranty/maple15/jre.X86_64_LINUX/bin/java: Permission denied

```but get a permission denied error (I've also tried doing this step before renaming the folders, same error).  Running maple as root doesn't even help.

Any ideas?

---

### Post by dcstar on 2013-01-19
> **carranty said:**
> I'm trying to install a copy of Maplesoft's Maple 15 onto my home computer.  This is a legal copy, obtained from my university library.  It comes on a CD, which contains an .bin file that installs the software onto my system.  Installation goes fine, but when I run the program I get the following error

```
carranty@Carranty-Desktop:~/maple15$ **./bin/xmaple** 
/home/carranty/maple15/bin/maple: 1: eval: /home/carranty/maple15/jre.X86_64_LINUX/bin/java: not found
```
..........
Any ideas?

Look at that file and see if it is a script with the Java path hard coded.

---

### Post by carranty on 2013-01-20
> **dcstar said:**
> Look at that file and see if it is a script with the Java path hard coded.

I don't understand scripts well enough to know what this does, but here are the contents of the xmaple file

```
#!/bin/sh

# Copyright (c) 1993-2010 by Maplesoft, a division of Waterloo Maple Inc.
# All rights reserved. Unauthorized duplication prohibited.
# Permission is granted to modify this file to be appropriate
# for use at the installation for which Maple was purchased.

# This script runs Maple with the Java interface.
MAPLE='/home/carranty/maple15'
export MAPLE 

"${MAPLE}/bin/maple" -x "$@"

```

---

### Post by carranty on 2013-01-20
Also, changing permissions on the java file leads to a segmentation fault (I'm not sure what these are)

```
carranty@Carranty-Desktop:~/maple15/bin$ ./maple -x
./maple: 1: eval: /home/carranty/maple15/jre.X86_64_LINUX/bin/java: Permission denied
carranty@Carranty-Desktop:~/maple15/bin$ sudo chmod 777 ../jre.X86_64_LINUX/bin/java
carranty@Carranty-Desktop:~/maple15/bin$ ./maple -x
Segmentation fault (core dumped)
carranty@Carranty-Desktop:~/maple15/bin$
```

---

