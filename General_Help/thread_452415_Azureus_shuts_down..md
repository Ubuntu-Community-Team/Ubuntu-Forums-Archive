---
title: "Azureus shuts down."
date: 2007-05-23
forum: General Help
---

### Post by Pixelstar on 2007-05-23
Hey Everybody 

I cant start my azureus, it shuts down after starting.. gets this in the terminal
-----------------------------------------------------
victor@cookie:~$ azureus
/home/victor/.themes/Carbonite/gtk-2.0/gtkrc:72: Kunne ikke finde billedfil i pixmap_path: "efefef"
/home/victor/.themes/Carbonite/gtk-2.0/gtkrc:1194: Kunne ikke finde billedfil i pixmap_path: "ProgressBar/progressbar-vert.png"
/home/victor/.themes/Carbonite/gtk-2.0/gtkrc:1198: Background image options specified without filename
#
# HotSpot Virtual Machine Error, Internal Error
# Please report this error at
# [http://www.blackdown.org/cgi-bin/jdk](http://www.blackdown.org/cgi-bin/jdk)
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#
# Error ID: 43113F32554E54494D45110E4350500308
#
# Problematic Thread: prio=5 tid=0x0805be10 nid=8030 runnable 
#

Heap at VM Abort:
Heap
 def new generation   total 576K, used 233K [0xab950000, 0xab9f0000, 0xabe30000)
  eden space 512K,  41% used [0xab950000, 0xab9849d8, 0xab9d0000)
  from space 64K,  35% used [0xab9e0000, 0xab9e5a80, 0xab9f0000)
  to   space 64K,   0% used [0xab9d0000, 0xab9d0000, 0xab9e0000)
 tenured generation   total 4848K, used 4008K [0xabe30000, 0xac2ec000, 0xaf950000)
   the space 4848K,  82% used [0xabe30000, 0xac21a040, 0xac21a200, 0xac2ec000)
 compacting perm gen  total 12288K, used 12142K [0xaf950000, 0xb0550000, 0xb3950000)
   the space 12288K,  98% used [0xaf950000, 0xb052b858, 0xb052ba00, 0xb0550000)
Aborted (core dumped)
---------------------------------------------------

---

### Post by anaconda on 2007-05-23
The easiest solution to this problem is:
Ktorrent

cant help with your azureus problem.. execpt.. which java are you using? The sun java works best.

---

### Post by dodgePT on 2007-05-23
I solved that problem with a solution found in [this thread]("http://ubuntuforums.org/showthread.php?t=436749&highlight=azureus2.jar").
You have to replace azureus2.jar in /usr/share/java/ with a azureus2 provided by sourceforge.
Anyway, make sure you have java6 (1.6) installed.

---

