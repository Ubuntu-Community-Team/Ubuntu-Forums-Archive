---
title: "Azureus loads then crashes"
date: 2007-01-07
forum: General Help
---

### Post by MetalSlugX on 2007-01-07
Here is the error from the console when I run it from the console

ben@ben-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# HotSpot Virtual Machine Error, Internal Error
# Please report this error at
# [http://www.blackdown.org/cgi-bin/jdk](http://www.blackdown.org/cgi-bin/jdk)
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#
# Error ID: 43113F32554E54494D45110E4350500308
#
# Problematic Thread: prio=5 tid=0x0805bda8 nid=29669 runnable 
#

Heap at VM Abort:
Heap
 def new generation   total 576K, used 525K [0xab980000, 0xaba20000, 0xabe60000)
  eden space 512K,  92% used [0xab980000, 0xab9f6f98, 0xaba00000)
  from space 64K,  77% used [0xaba10000, 0xaba1c688, 0xaba20000)
  to   space 64K,   0% used [0xaba00000, 0xaba00000, 0xaba10000)
 tenured generation   total 3820K, used 2310K [0xabe60000, 0xac21b000, 0xaf980000)
   the space 3820K,  60% used [0xabe60000, 0xac0a19a0, 0xac0a1a00, 0xac21b000)
 compacting perm gen  total 12288K, used 12157K [0xaf980000, 0xb0580000, 0xb3980000)
   the space 12288K,  98% used [0xaf980000, 0xb055f580, 0xb055f600, 0xb0580000)
Aborted (core dumped)

---

### Post by meng on 2007-01-07
You may wish to install Sun Java rather than relying on Blackdown Java.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by griffinbeans on 2007-01-08
There is a known bug in the Azureus package in the repo.
Here is the workaround link: [http://ubuntuforums.org/showthread.p...hlight=azureus](http://ubuntuforums.org/showthread.p...hlight=azureus)

---

### Post by griffinbeans on 2007-01-08
try this
[http://ubuntuforums.org/showthread.php?t=283364](http://ubuntuforums.org/showthread.php?t=283364)

---

