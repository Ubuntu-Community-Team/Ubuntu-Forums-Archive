---
title: "Kernel compilation"
date: 2007-04-12
forum: General Help
---

### Post by abhishek456 on 2007-04-12
When i tried to compile my kernel i got an error

When i typed make xconfig i got the fallowing 

> 
root@home-desktop:/usr/src/linux-2.6.20.6# make xconfig
/usr/src/linux-2.6.20.6/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-2.6.20.6/scripts/gcc-version.sh: line 12: gcc: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2
root@home-desktop:/usr/src/linux-2.6.20.6#



---

### Post by rufius on 2007-04-12
type this:

```
sudo apt-get install gcc
```

Then try the 'make xconfig' again.

---

### Post by abhishek456 on 2007-04-13
ok i will try this

---

### Post by abhishek456 on 2007-04-13
ok i have ran "sudo apt-get install gcc" in the terminal. But after this running "make xconfig" gave me this

> 
root@home-desktop:/usr/src/linux-2.6.20.6# make xconfig
  CHECK   qt
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
/bin/sh: g++: command not found
make[1]: *** [scripts/kconfig/qconf.o] Error 127
make: *** [xconfig] Error 2
root@home-desktop:/usr/src/linux-2.6.20.6#



---

### Post by Seisen on 2007-04-13
You can follow this guide and I know it works because I have used it before.

[http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel")

---

