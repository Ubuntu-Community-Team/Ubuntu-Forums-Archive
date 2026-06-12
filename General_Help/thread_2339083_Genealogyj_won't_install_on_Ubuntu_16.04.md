---
title: "Genealogyj won't install on Ubuntu 16.04"
date: 2016-10-04
forum: General Help
---

### Post by alanjackson on 2016-10-04
Just upgraded to 16.04 LTS, and genealogyj wouldn't run, so I tried to update it, and that fails as well.

```
$ java -version
openjdk version "9-internal"
OpenJDK Runtime Environment (build 9-internal+0-2016-04-14-195246.buildd.src)
OpenJDK 64-Bit Server VM (build 9-internal+0-2016-04-14-195246.buildd.src, mixed mode)
```

```
$ java -jar genj_install-6755.jar
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f88a222a009, pid=15624, tid=15625
#
# JRE version: OpenJDK Runtime Environment (9.0) (build 9-internal+0-2016-04-14-195246.buildd.src)
# Java VM: OpenJDK 64-Bit Server VM (9-internal+0-2016-04-14-195246.buildd.src, mixed mode, tiered, compressed oops, g1 gc, linux-amd64)
# Problematic frame:
# C  [libjava.so+0x1d009]  JNU_GetEnv+0x19
#
# Core dump will be written. Default location: Core dumps may be processed with "/usr/share/apport/apport %p %s %c %P" (or dumping to /home/ajackson/genj/core.15624)
#
# An error report file with more information is saved as:
# /home/ajackson/genj/hs_err_pid15624.log
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)
```

---

### Post by echotech2 on 2016-10-05
Genealogyj doesn't seem to have been updated since 2010. might have something to do with it.

---

