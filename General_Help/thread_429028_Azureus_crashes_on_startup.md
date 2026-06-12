---
title: "Azureus crashes on startup"
date: 2007-04-30
forum: General Help
---

### Post by jgbiggs on 2007-04-30
I am trying to run the latest from sourceforge and get this error:

jgbiggs@ubuntu-desktop:~/azureus$ ./azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/jgbiggs/azureus/Azureus2.jar" -Djava.library.path="/home/jgbiggs/azureus" -Dazureus.install.path="/home/jgbiggs/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Display
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)
Azureus TERMINATED.
jgbiggs@ubuntu-desktop:~/azureus$

---

### Post by vratnica on 2007-05-01
have you tried the instructions here:

[http://ubuntuforums.org/showthread.php?t=353197&highlight=azureus+log](http://ubuntuforums.org/showthread.php?t=353197&highlight=azureus+log)

---

