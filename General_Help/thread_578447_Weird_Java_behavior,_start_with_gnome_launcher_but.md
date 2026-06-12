---
title: "Weird Java behavior, start with gnome launcher but not the terminal"
date: 2007-10-17
forum: General Help
---

### Post by Biochem on 2007-10-17
I need to launch java application from the terminal. With Feisty 32 bit there was no problem but with Gutsy 64 bit I always get core dump.

An exemple of this would be Jabref (it's in synaptic). It installation creates a laucher in the office menu. If I click it, the application launch, I can also start the application by doing alt+F2 jabref. But if I type jabref in the terminal I always get a core dump.

```
Biochem@nefuats:~$ jabref
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b58b7f52e25, pid=29262, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid29262.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

I get this behavior with other java application. The problem is that I have to launch ImageJ though ssh and therefor need to be able to use the terminal. Does anyone know a solution to this?

Thanks

---

