---
title: "[SOLVED] JDK problems on Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by IllegalCharacter on 2007-10-20
I've just installed Gutsy on my AMD64, but I'm having some real troubles getting Java and Netbeans to work. I installed the Sun packages (bin, jre, jdk) all at version 6 and got rid of all the gij/gcj stuff because they screw up Azureus (which works fine right now). So Java works well - besides the Firefox plugin not working - but when I try to run Netbeans, I get this lovely error:
```

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002acc87edee25, pid=10497, tid=1092860240
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid10497.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

I tried reverting back to Java 1.5, but that gave me the problems with Swing components not appearing. Does anybody have any ideas? I feel like somebody who just upgraded to Windows Vista and suddenly nothing works anymore (I haven't even tried to use my printer yet :( ).

---

### Post by IllegalCharacter on 2007-10-21
Nevermind, I figured it out. Apparently the Sun JDK 6 package doesn't actually install the JDK, I had to do it manually. Also the MToolkit fix actually breaks Java 6. So don't do it.

---

### Post by VHans on 2007-10-31
> **IllegalCharacter said:**
> Nevermind, I figured it out. Apparently the Sun JDK 6 package doesn't actually install the JDK, I had to do it manually. Also the MToolkit fix actually breaks Java 6. So don't do it.

Can you tell me how you did this? I am having a similar problem on my 32bit Gutsy.

---

### Post by IllegalCharacter on 2007-10-31
What are you trying to do? Install the JDK?

---

