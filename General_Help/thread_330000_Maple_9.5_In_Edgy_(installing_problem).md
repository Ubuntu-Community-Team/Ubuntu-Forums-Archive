---
title: "Maple 9.5 In Edgy (installing problem)"
date: 2007-01-02
forum: General Help
---

### Post by reza81 on 2007-01-02
I have folowed the [instructions]("http://ubuntuforums.org/showthread.php?t=274407&highlight=maple")
as described & got some error about libc.so.6 as you can see hier below

```

reza@reza-desktop:~/tmpmaple$ sudo sh installMapleLinuxSU
Password:
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
/tmp/install.dir.12042/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
reza@reza-desktop:~/tmpmaple$

```

Can someone please help me with this?

---

### Post by reza81 on 2007-01-02
this is the way to do it >>> [http://ubuntuforums.org/showthread.php?t=283473&highlight=maple]("http://ubuntuforums.org/showthread.php?t=283473&highlight=maple")

it works great :-D

---

