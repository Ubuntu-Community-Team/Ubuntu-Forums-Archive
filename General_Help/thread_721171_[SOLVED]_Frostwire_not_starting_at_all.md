---
title: "[SOLVED] Frostwire not starting at all"
date: 2008-03-11
forum: General Help
---

### Post by mrfraser89 on 2008-03-11
Hey guys, I downloaded Sun Java 6 (running on 64 bit gutsy 7.10)

Running in terminal outputs the following



Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b6ba8ad5e25, pid=8952, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid8952.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  8952 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)


Running from the start menu just does... nothing...

From what I can see it's a problem with Java but what it is, I'm not sure, tried reinstalling with synaptic as well as complete uninstall and install, no luck (of Java).

---

### Post by mrfraser89 on 2008-03-11
No ideas :( ?

---

### Post by mrfraser89 on 2008-03-11
Solved by downloading the package 

```
ia32-sun-java6-bin
```

(sun-java6-bin and sun-java6-jre were already installed)



Then running the code

```



sudo update-alternatives --config java


```

and selecting ia32 as the place to run java. Success :D

---

