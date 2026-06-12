---
title: "azureus help?"
date: 2005-04-28
forum: General Help
---

### Post by NorthernSoul on 2005-04-28
hello everyone. ive been running ubuntu for a little while, and tried to run azureus, but im having some trouble. i ran it through the terminal so i could give you the error message, so here it is:
```
Starting Azureus...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/java/jre/bin/
Suitable java version found  [/usr/java/jre/bin/java = 1.4.2]
Configuring environment...
Loading Azureus:
/usr/java/jre/bin/java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar:/opt/azureus/swt-mozilla.jar:/opt/azureus/swt-pi.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
DEBUG::Thu Apr 28 19:42:05 MDT 2005
  java.lang.ClassNotFoundException: com.sun.net.ssl.internal.ssl.Provider
        at java.net.URLClassLoader.findClass(URLClassLoader.java:375)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:562)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:442)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:494)
        at java.lang.Class.forName1(Native Method)
        at java.lang.Class.forName(Class.java:180)
        at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise(SESecurityManagerImpl.java:88)
        at org.gudy.azureus2.core3.security.SESecurityManager.initialise(SESecurityManager.java:50)
        at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties(ConfigurationChecker.java:179)
        at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise(ConfigurationManager.java:90)
        at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance(ConfigurationManager.java:46)
        at org.gudy.azureus2.core3.config.COConfigurationManager.initialise(COConfigurationManager.java:41)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:102)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:67)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:35)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:100)

JVMDG217: Dump Handler is Processing a Signal - Please Wait.
JVMDG303: JVM Requesting Java core file
JVMDG304: Java core file written to /tmp/javacore.20050428.194206.16062.txt
JVMDG215: Dump Handler has Processed Exception Signal 4.
/opt/azureus/azureus: line 107: 16062 Illegal instruction     ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.
```
any ideas? and keep in mind that although ive learned quite a bit of unix on my own recently, im still pretty green.

---

### Post by bored2k on 2005-04-28
How did you install java ?

** I suggest you install sun-j2re1.5 from backports --something like:
```
sudo echo deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted >> /etc/apt/sources.list && sudo echo deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted >> /etc/apt/sources.list && sudo apt-get update && apt-get install sun-j2re1.5
```

---

### Post by NorthernSoul on 2005-04-28
i installed it with the help of [this thread](http://ubuntuforums.org/showthread.php?t=23769). is that download for ppc? when i was searching that was the best i found on powerpc.

---

