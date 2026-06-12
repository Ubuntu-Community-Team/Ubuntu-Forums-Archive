---
title: "LimeWire not working"
date: 2005-05-05
forum: General Help
---

### Post by WildTangent on 2005-05-05
i followed the unofficial guide to the letter when i install limewire, when i click on it in the applications menu, nothing happens. any help would be appreciated.

-Wild

---

### Post by DutchLau on 2005-05-05
Hello Wildtangent,

Did you install Java? If so, try running LimeWire in your terminal (check to see where the command is by righclicking on limewire in applications=> internet
 =>limewire) and post any error messages. 

DutchLau

---

### Post by WildTangent on 2005-05-05
oh..might have forgotten that one...

-Wild

---

### Post by WildTangent on 2005-05-05
i cant get the JRE, i tried downloading it from the site the guide gives you, no dice

-Wild

---

### Post by bored2k on 2005-05-06
[QUOTE=WildTangent]i cant get the JRE, i tried downloading it from the site the guide gives you, no dice

-Wild[/QUOTE]
 1. Download from jdong's backports [sudo apt-get install sun-j2re1.5]
 or
2. Create your own java package
[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

---

### Post by XDevHald on 2005-05-11
[QUOTE=bored2k]1. Download from jdong's backports [sudo apt-get install sun-j2re1.5]
 or
2. Create your own java package
[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)[/QUOTE]
 Thanks for the the command bored, kinda forgot that one myself, and yes it does work btw, but the backports are terribly slow :p

---

### Post by bored2k on 2005-05-11
[QUOTE=BB]Thanks for the the command bored, kinda forgot that one myself, and yes it does work btw, but the backports are terribly slow :p[/QUOTE]
 I alwayss build my own java package ^_^. I wasn't happy when backport's tried to overwrite my package, so I got *-en colère-* and removed them.

---

### Post by hoosemon61 on 2005-05-11
[QUOTE=DutchLau]Hello Wildtangent,

Did you install Java? If so, try running LimeWire in your terminal (check to see where the command is by righclicking on limewire in applications=> internet
 =>limewire) and post any error messages. 

DutchLau[/QUOTE]
 I had the same problem as WildTangent.  I had already downloaded a new JRE (1.5.0.02).

I took your advice and ran the command line in terminal.  

Here's the error message i got: 

[I]Starting LimeWire...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in /usr/java/ heirarchy
You need to upgrade to JRE 1.4.x or newer from http//www.java.com[/I]


Sadly I was at 1.4.x before I installed 1.5.0 as directed by the LimeWire site.

Did I install Java in the wrong place?

I am an extreme newby...

---

### Post by zab on 2005-05-17
[QUOTE=hoosemon61]Sadly I was at 1.4.x before I installed 1.5.0 as directed by the LimeWire site.

Did I install Java in the wrong place?

I am an extreme newby...[/QUOTE]

The installation instructions and the startup script are designed for rpm-based distros.  If someone wishes to help us upgrade the runLime.sh to work for .deb-based distros we'll include it in the next version.

---

### Post by bored2k on 2005-05-17
[QUOTE=zab]The installation instructions and the startup script are designed for rpm-based distros.  If someone wishes to help us upgrade the runLime.sh to work for .deb-based distros we'll include it in the next version.[/QUOTE]
 runLime.sh runs if I double click on it here. If I try creating a script I do have to point it in the right direction first, but after I made my jpackage, I get no problems at all.

---

### Post by zab on 2005-05-18
[QUOTE=bored2k]runLime.sh runs if I double click on it here. If I try creating a script I do have to point it in the right direction first, but after I made my jpackage, I get no problems at all.[/QUOTE]

What I meant is to make the script find the appropriate location itself without the user having to know it.  The RPMs from Sun always install java in /usr/java, so the script right now iterates through the sub-directories of that location and searches for an appropriate jvm.  If there is a default location where the jre should be in debian-derived systems, the script would ideally search there - this way the user can use apt to install the jre, alien limewire and have it working out of the box.

---

