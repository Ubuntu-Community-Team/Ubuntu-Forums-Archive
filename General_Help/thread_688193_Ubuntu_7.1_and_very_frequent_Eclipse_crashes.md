---
title: "Ubuntu 7.1 and very frequent Eclipse crashes"
date: 2008-02-05
forum: General Help
---

### Post by pepez on 2008-02-05
I have newly installed Ubuntu 7.1 with Kubuntu added on. Eclipse versions tested were 3.3 and 3,4M4. I also tried downgrading explained in [http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020) but no luck.

The same crash happens under both Java 1.5 and Java 6. Also, memory setting do not have any effect on this.

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb7e72028, pid=6407, tid=3084916400
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_13-b05 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x70028]  strcmp+0x8
#
# An error report file with more information is saved as hs_err_pid6407.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#


# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7e26028, pid=6250, tid=3084450704
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x70028]  strcmp+0x8
#
# An error report file with more information is saved as hs_err_pid6250.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

Any suggestions?

---

