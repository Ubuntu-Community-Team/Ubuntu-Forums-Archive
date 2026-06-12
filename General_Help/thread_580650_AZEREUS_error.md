---
title: "AZEREUS error"
date: 2007-10-18
forum: General Help
---

### Post by jayaramk on 2007-10-18
when i tried opening azereus from the command line i get the following error... it opens but closes immediately....


jayaram@jayaram-desktop:~$ azureus
changeLocale: *Default Language* != English (India). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (India)' (en_IN), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=8717, tid=3085200272
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid8717.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by conehead77 on 2007-10-19
Delete all log files from the ~/.azureus/logs/ directory.
Then start Azureus again.

---

