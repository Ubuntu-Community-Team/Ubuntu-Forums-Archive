---
title: "java problem(azureus)"
date: 2007-02-25
forum: General Help
---

### Post by rabid9797 on 2007-02-25
i just recently upgraded from java 1.4.2 to 1.5.0(so i could use limewire), and now azureus crashes. 

here's the error i get when i try to start azureus:
```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0550d02, pid=14200, tid=3084859056
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid14200.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

im sure this is a common issue but doing a search didn't show up anything in the first two or three threads.
could anyone point out a fix?

---

### Post by Timtro on 2007-03-11
Having the same problem.

---

### Post by Timtro on 2007-03-11
Solution:

I tracked down the jar file using,

```
which azureus
```

which shows you the startup script, which shows the jar file in 

/usr/share/java/Azureus2.jar

Just download the latest jar from the azureus sourceforge website and rename it to Azureus2.jar, and replace your own with the new one.

---

### Post by rcpilot on 2007-04-01
> **Timtro said:**
> Solution:

I tracked down the jar file using,

```
which azureus
```

which shows you the startup script, which shows the jar file in 

/usr/share/java/Azureus2.jar

Just download the latest jar from the azureus sourceforge website and rename it to Azureus2.jar, and replace your own with the new one.
This seems to be working but we'll see if it keeps on working.  I believe it has something to do with when I installed the 1.4 JRE, because that didn't install with azureus but I later installed it so I could have the latest stable version of java for my browser.  And although I'm not sure exactly when the problem started it definitely happened after that.

---

### Post by Franscisco on 2007-04-14
How does Azereus work?

---

