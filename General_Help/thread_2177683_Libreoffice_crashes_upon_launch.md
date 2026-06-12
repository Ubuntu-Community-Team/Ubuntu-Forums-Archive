---
title: "Libreoffice crashes upon launch"
date: 2013-09-29
forum: General Help
---

### Post by electricmaster on 2013-09-29
I'm having trouble running Libreoffice. Once I launch it (from terminal, desktop icons, using existing files), the splash screen pops up and hangs for a few seconds, and then crashes. It used to work, but it doesn't anymore.
I ran it from the terminal and this is what I get:
```
maclm01@maclm01-AO532h:~$ libreoffice -V --writer
terminate called after throwing an instance of 'com::sun::star::uno::DeploymentException'
```
This happens with all LibreOffice programs.
I've tried purging/reinstalling several times and I've deleted ~/.libreoffice and ~/.config/libreoffice.
```
ProblemType: CrashArchitecture: i386
CrashCounter: 1
Date: Sun Sep 29 19:52:55 2013
DistroRelease: Ubuntu 13.04
ExecutablePath: /usr/lib/libreoffice/program/soffice.bin
ExecutableTimestamp: 1365705842
ProcCmdline: /usr/lib/libreoffice/program/soffice.bin --writer --splash-pipe=6
ProcCwd: /home/maclm01
ProcEnviron:
 LC_TIME=en_US.UTF-8
 LANGUAGE=en
 LC_MONETARY=en_US.UTF-8
 PATH=(custom, no user)
 XDG_RUNTIME_DIR=<set>
 LC_ADDRESS=en_US.UTF-8
 LANG=en_US.UTF-8
 LC_TELEPHONE=en_US.UTF-8
 SHELL=/bin/bash
 LC_NAME=en_US.UTF-8
 LC_MEASUREMENT=en_US.UTF-8
 LC_IDENTIFICATION=en_US.UTF-8
 LC_NUMERIC=en_US.UTF-8
 LC_PAPER=en_US.UTF-8
 LD_LIBRARY_PATH=<set>
```

---

### Post by Jonor on 2013-10-01
Have you ruled out insufficient cpu/memory ?

Put in a terminal
```
free
```

and watch the top two or three lines as LibreOffice is subsequently opened.

---

### Post by electricmaster on 2013-10-03
> **Jonor said:**
> Have you ruled out insufficient cpu/memory ?

Put in a terminal
```
free
```

and watch the top two or three lines as LibreOffice is subsequently opened.

Hmm... the memory usage didn't change all that much. It worked before on this machine, so I don't see that being an issue.

---

