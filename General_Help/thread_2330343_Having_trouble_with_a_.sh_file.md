---
title: "Having trouble with a .sh file"
date: 2016-07-10
forum: General Help
---

### Post by Mazate on 2016-07-10
I'm trying to install some genealogy software and I'm having a little trouble with it.  It's a .sh file.  I make the file executable and then this is what I'm getting:

```
david@david-desktop:~/Downloads$ ./Indexing_unix.sh
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.6 and at most 1.6.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/david/.install4j

```
Admittedly my knowledge of Java is limited but I do have Java 8 installed.  Apparently there is something I'm missing.  I'm not sure what the process would be to "define INSTALL4J_JAVA_HOME to point to a suitable JVM."  

Any help is most appreciated!

---

### Post by &amp;KyT$0P# on 2016-07-10
It's saying it requires specifically Java 6... and you have only Java 8.

What version of Ubuntu are you using?

---

### Post by QIII on 2016-07-10
Java 6 is past End of Life and was rife with security problems long before that.

Don't use it and don't use anything that depends on it.  Whatever your script is for, it has not been maintained and is not safe.

---

### Post by Mazate on 2016-07-10
I'm using 16.04.  I need to update my profile.  Anyway, if it requires Java 6 then I guess I'm screwed.  Ok, thanks for the help.

---

