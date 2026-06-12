---
title: "Problem on running java"
date: 2017-11-30
forum: General Help
---

### Post by satimis on 2017-11-30
Hi,

JStock
[https://jstock.org/](https://jstock.org/)

OS - Ubuntu 16.04 desktop 64bit
Javs - openjdk-9-jre

Problem on running;
$ ./jstock```

# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f3819d880c9, pid=20237, tid=20290
#
# JRE version: OpenJDK Runtime Environment (9.0) (build 9-internal+0-2016-04-21-232247.buildd.src)
# Java VM: OpenJDK 64-Bit Server VM (9-internal+0-2016-04-21-232247.buildd.src, mixed mode, tiered, compressed oops, g1 gc, linux-amd64)
# Problematic frame:
# C  [libjava.so+0x1d0c9]  JNU_GetEnv+0x19
#
# Core dump will be written. Default location: Core dumps may be processed with "/usr/share/apport/apport %p %s %c %d %P" (or dumping to /home/satimis/jstock/core.20237)
#
# An error report file with more information is saved as:
# /home/satimis/jstock/hs_err_pid20237.log
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
./jstock.sh: line 47: 20237 Aborted                 (core dumped) $_JAVA_EXEC $_VMOPTIONS -jar jstock.jar

```

Please help.  Thanks

I can't upload the log file hs_err_pid20237.log here. I don't know why?  The file size is only 89.7kB. Also I have renamed it as hs_err_pid20237.txt without success.

Regards
satimis

---

### Post by slickymaster on 2017-11-30
*Thread moved to **General Help**.*

---

