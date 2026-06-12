---
title: "Some programs not recognizing printer"
date: 2007-07-28
forum: General Help
---

### Post by Fraoch on 2007-07-28
Hello:

Some of my programs do not recognize that I have a printer installed (Epson Stylus Color 660).

The OS certainly recognizes it and auto-detects it, Swiftweasel (web broswer) does, so I assume Firefox does as well, GIMP does, evince does and OpenOffice does.  I'm using the Gutenprint CUPS expert drivers.

However I have two CAD programs which do not: QCAD and XTrkCad.  QCAD's dialog box doesn't show any printers installed at all (see screenshot) and XTrkCad has two options: FILE and "ls".  FILE prints to file and "ls" doesn't do anything, see the second screenshot.

Any suggestions?  Am I missing some critical CUPS or HPLIP components?  How does Ubuntu notify all applications of installed printers?

The "ls" indication seems to specify some sort of low-level name, kind of like /dev/sda1 for drives...I looked in /dev/ but didn't see anything starting with "ls".

Should I go to the individual forums of these programs?

Thanks.

---

### Post by Fraoch on 2007-07-28
It may be a 64-bit thing.  The printer is installed on my Ubuntu 7.04 64-bit machine and I'm trying to share it with my 32-bit machine.

On the 32-bit machine, QCAD recognizes the printer and can print to it?  Yet the host machine that the printer is installed on can't.  Bizarre?

---

### Post by Fraoch on 2007-07-29
These were both problems related to the programs.  Both fixed.

QCAD: [http://tech.groups.yahoo.com/group/qcad-user/message/1821](http://tech.groups.yahoo.com/group/qcad-user/message/1821)

XTrkCad: [http://groups.yahoo.com/group/XTrkCad/message/2516](http://groups.yahoo.com/group/XTrkCad/message/2516)

---

