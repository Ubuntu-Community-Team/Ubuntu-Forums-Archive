---
title: "Help installing DETools for Differential Equations"
date: 2007-10-07
forum: General Help
---

### Post by Pinoy915 on 2007-10-07
The CD came with no documentation about the dependencies for the Linux version. I tried using getlibs but all I get was: "Cannot determine the dependencies required by this program, it may be a script:"

I installed libc6 but still no progress. Here's what happens when I run the bin:

```
carlo@carlo-desktop:/media/cdrom/linux$ sh install.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.5641/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

---

### Post by Pinoy915 on 2007-10-11
Anyone know what the problem may be?

---

### Post by jmank88 on 2008-02-03
no idea, im getting the exact same problem.

---

