---
title: "Compiling JDK on 18.04 reboots the system"
date: 2019-02-08
forum: General Help
---

### Post by kovalex on 2019-02-08
Hello folks, I'm trying to compile JDK from sources ([https://hg.openjdk.java.net/jdk9/jdk9/](https://hg.openjdk.java.net/jdk9/jdk9/)) and routinely getting reboot without any clue left n /var/log/*.
I've tried to limit compilation with JDK's specific settings (--with-num-cores, --with-memory-size, --with-jobs) but still compilation (make all) reboots system in the middle.
Any tips how to isolate this?

---

