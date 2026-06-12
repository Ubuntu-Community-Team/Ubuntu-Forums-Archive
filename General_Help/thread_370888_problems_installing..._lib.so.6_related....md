---
title: "problems installing... lib*.so.6 related..."
date: 2007-02-26
forum: General Help
---

### Post by tocleora on 2007-02-26
I'm trying to install Zend Guard in Edgy, and I'm getting this error:

```
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
/tmp/install.dir.14569/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

Doing some minor research I thought it might be java related, java-common is installed.  Any thoughts?

---

### Post by tocleora on 2007-02-27
In case anyone else has this problem, here's the solution:

[http://www.zend.com/support/knowledgebase.php?kbid=226&view_only=1](http://www.zend.com/support/knowledgebase.php?kbid=226&view_only=1)

---

### Post by Eversmann on 2007-03-01
Thanks for the reply, that solved my problem.

---

### Post by MxGB on 2007-03-10
Thanks for the link, it worked for me (Zend Guard 4.0.1 on Edgy).

---

### Post by crazy ivan on 2007-11-03
Funny to note, that the same problem arises with installing Maple 9.5 on Ubuntu 7.10. Still the solution is the same :)

You only have to applie the procedure from [http://www.entwickler-blog.de/archiv/146-Zend-Studio-nawk-error-while-loading-shared-libraries-libm.so.6.html]("http://www.entwickler-blog.de/archiv/146-Zend-Studio-nawk-error-while-loading-shared-libraries-libm.so.6.html")
or the one posted above to the file

```

Linux/Disk1/InstData/VM/LinuxInstaller.bin

```

on your harddisk copy of the CD. Afterwards it installs properly and "/bin/xmaple" runs without hassles.

---

