---
title: "Azureus: Load...Unload!"
date: 2006-12-13
forum: General Help
---

### Post by Tekovro on 2006-12-13
well ive tried searching through the forum for a similar case but i did not find anything that fixed this.

basically i click to open azureus and it loads nice and fast, then once it's done it shows the program for 1 second and then poof, it's off. im not sure why it does that but it's not what i want it to do(duh) 

Im still rather new to ubuntu, or linux for that matter. so please dont get too technical, dumb it down a bit so i can get this fixed. thank you very much!

---

### Post by pay on 2006-12-13
Can you open up the terminal and then type in ```
azureus
```to see what the problem is. Also make sure that you have some variation of java installed.

---

### Post by Tekovro on 2006-12-13
azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x8b059d02, pid=14963, tid=3085223600
#
# Java VM: Java HotSpot(TM) Server VM (1.5.0_08-b03 mixed mode)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid14963.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by Tekovro on 2006-12-13
i tried replacing the azureus2.jar file but it wont let me. says i dont have permission because im not the owner.. is bill gates behind this?

---

### Post by pay on 2006-12-13
Ubuntu has good security practises that is why you are not the owner of the file. To get ownership you can add sudo infront of your command, or if you like to do things graphically type```
gksudo nautilus
```Sorry but I'm not sure what the error message means. Maybe an improper installation of java.

---

### Post by Get_Ya_Wicked_On on 2006-12-13
Trust me, it's on here somewhere. I had the same problem.

Someone posted a way to download it from the sourceforge site & it worked perfectly.

In fact, [http://www.ubuntuforums.org/showthread.php?t=313654&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=313654&highlight=azureus)

Look toward the bottom. Hm, on the first page of a search for "azureus".

---

