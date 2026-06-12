---
title: "Azureus crashes"
date: 2007-01-05
forum: General Help
---

### Post by HIGHLIFE on 2007-01-05
When I try to run azureus, the splash screen will load and then it crashes. 
Here is the console output:
```
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x8b28cd02, pid=13732, tid=3085113008
#
# Java VM: Java HotSpot(TM) Server VM (1.5.0_08-b03 mixed mode)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]

```

Thx for the help.

---

### Post by Josey on 2007-01-05
I had the same problem and here is the fix...

download the latest azureus here.
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)
rename Azureus2501-B54.jar to Azureus2.jar and overwrite the old one located in /usr/share/java/

---

### Post by HIGHLIFE on 2007-01-05
That worked thx a ton!

---

### Post by Josey on 2007-01-05
Not a problem.

---

### Post by apost on 2007-03-22
That was the trick.Thanx.:)

---

### Post by DynamicJ on 2007-03-25
hi I am trying to overwrite in usr/share/java, and it says "denied:  you do not have permission to write to this folder"

wtf??

---

### Post by dedmonds on 2007-03-26
Thanks, Josey. That solved the problem for me, too.

DynamicJ: I was able to overwrite the file from the terminal command line using the sudo command.

---

### Post by bcrom on 2007-04-04
Worked for me too.  Thanks.

---

### Post by ravimannan2002 on 2007-08-26
thanks!

---

### Post by Digitallysick on 2007-08-26
I had alot of azureus problems, when it crashed i would have to "delete" the logs over and over to get it to start again, i finally switched to ktorrent, its just better for me, i even get faster downloads

---

