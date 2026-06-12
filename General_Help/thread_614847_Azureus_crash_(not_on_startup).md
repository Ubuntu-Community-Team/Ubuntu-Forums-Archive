---
title: "Azureus crash (not on startup)"
date: 2007-11-16
forum: General Help
---

### Post by martibs on 2007-11-16
When I try to view the download details of a spesific torrent by double clicking it, Azureus just immidiatly crashes, with no error message. Removing the ~/.azureus folder did not have an effect on the problem. This is the output after running Azureus from command line:

```
$ azureus 
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00002b0aa9ac27a5, pid=29040, tid=47324792412912
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.5.0_13-b05 mixed mode)
# Problematic frame:
# V  [libjvm.so+0x3b37a5]
#
# An error report file with more information is saved as hs_err_pid29040.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

---

### Post by martibs on 2007-11-19
Never mind, this was fixed in todays (or at least a recent) update.

---

