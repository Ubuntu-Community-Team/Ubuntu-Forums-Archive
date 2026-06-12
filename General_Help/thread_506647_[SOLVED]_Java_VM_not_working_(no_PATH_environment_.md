---
title: "[SOLVED] Java VM not working (no PATH environment var)"
date: 2007-07-21
forum: General Help
---

### Post by WinterWeaver on 2007-07-21
Hey all,

I'm trying to run a program that is Java based. I have all the sun-java stuff installed (version 6)

when I run the script, I get this error message:
```
$ ./PoseidonCE_6_0_1_Installer.bin 
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.

```

I've tried to add the path in /etc/environment
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin"
```

but it's still not working for me. Did I add the right path (there are so many directories =/   )

Thanks,

WW

---

### Post by WinterWeaver on 2007-07-22
Solution found after reboot

---

