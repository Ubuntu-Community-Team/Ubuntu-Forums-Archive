---
title: "aptana error message"
date: 2007-03-14
forum: General Help
---

### Post by LSparky on 2007-03-14
im trying to install Aptana.bin, I keep getting this output.
how come this happens?

jett@jett-desktop:~/Desktop$ sh Aptana_IDE_Setup.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.9497/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

---

### Post by 23meg on 2007-03-14
Take a look at [these instructions]("http://www.ubuntuforums.org/showthread.php?t=315444").

---

### Post by LSparky on 2007-03-14
hey thanks ill try that

---

### Post by adarkmethod on 2007-04-10
hey, im getting a weird aptana related error from Package Manager 

E: aptana: subprocess post-installation script returned error exit status 1

---

