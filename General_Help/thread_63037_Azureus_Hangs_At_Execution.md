---
title: "Azureus Hangs At Execution"
date: 2005-09-06
forum: General Help
---

### Post by Unit #134679 on 2005-09-06
When I try and run Azureus, it hangs and never opens. This is from the debug file:
```

[17:37:09] DEBUG::Tue Sep 06 17:37:09 EDT 2005
[17:37:09]   java.lang.ClassNotFoundException: com.sun.net.ssl.internal.ssl.Provider not found in [file:/usr/share/java/swt-gtk-3.1.jar, file:/usr/share/java/swt-pi-gtk-3.1.jar, file:/home/mark/.Azureus/Azureus2.jar, file:/usr/share/java/Azureus2.jar]
   at java.net.URLClassLoader.findClass (URLClassLoader.java:748)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:359)
   at java.lang.ClassLoader$1.loadClass (ClassLoader.java:1282)
   at java.lang.Class.forName (Class.java:352)
   at java.lang.Class.forName (Class.java:260)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise (SESecurityManagerImpl.java:88)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise (SESecurityManager.java:50)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties (ConfigurationChecker.java:185)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise (ConfigurationManager.java:93)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance (ConfigurationManager.java:49)
   at org.gudy.azureus2.core3.config.COConfigurationManager.getBooleanParameter (COConfigurationManager.java:86)
   at org.gudy.azureus2.core3.internat.LocaleUtil.LocaleUtil (LocaleUtil.java:96)
   at org.gudy.azureus2.core3.internat.LocaleUtil.static{} (LocaleUtil.java:34)
   at java.lang.VMClass.step8 (VMClass.java)
   at java.lang.Class.initialize (Class.java:145)
   at org.gudy.azureus2.core3.util.SystemProperties.getEnvironmentalVariable (SystemProperties.java:189)
   at org.gudy.azureus2.core3.util.SystemProperties.getUserPath (SystemProperties.java:88)
   at org.gudy.azureus2.core3.util.FileUtil.readResilientConfigFile (FileUtil.java:438)
   at org.gudy.azureus2.core3.util.FileUtil.readResilientConfigFile (FileUtil.java:408)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load (ConfigurationManager.java:100)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.load (ConfigurationManager.java:105)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.ConfigurationManager (ConfigurationManager.java:76)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance (ConfigurationManager.java:47)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise (COConfigurationManager.java:51)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl (AzureusCoreImpl.java:111)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create (AzureusCoreImpl.java:69)
   at com.aelitis.azureus.core.AzureusCoreFactory.create (AzureusCoreFactory.java:46)
   at org.gudy.azureus2.ui.swt.Main.Main (Main.java:35)
   at org.gudy.azureus2.ui.swt.Main.main (Main.java:98)
   at java.lang.VirtualMachine.invokeMain (VirtualMachine.java)
   at java.lang.VirtualMachine.main (VirtualMachine.java:92)
```

---

### Post by Weav on 2005-09-06
just a wild guess do you have java installed using the ubuntu guide?
Did you use "apt-get install" to install it?

---

### Post by Unit #134679 on 2005-09-06
Yes I did :)

---

### Post by Weav on 2005-09-06
[QUOTE=Unit #134679]Yes I did :)[/QUOTE]
hhhhmmm thats strange myabe do complete removal of azureus (as long as it doesn't take out any java or other important files) and maybe that will fix something.

---

### Post by Unit #134679 on 2005-09-06
Same thing

---

### Post by oliwally on 2005-09-07
I have exactly the same problem. I've tried reinstalling java and azureus - but no luck

---

### Post by Unit #134679 on 2005-09-07
Sucks dont it?

---

### Post by Simppa on 2005-09-19
I had this problem too, and i had the j2re problem too.

I resolved by:

Uninstalling liblog4j1.2-java and libcommons-cli-java. After that i installed those back manually. 

liblog4j1.2-java [HTML]http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fj%2Fjakarta-log4j1.2%2Fliblog4j1.2-java_1.2.9-1_all.deb&md5sum=072ea881fb91c39980ff1c281d3dcc7d&arch=all&type=main[/HTML] 
And
ibcommons-cli-java
[HTML]http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Flibc%2Flibcommons-cli-java%2Flibcommons-cli-java_1.0-7_all.deb&md5sum=94bde329b4eb02622befe782e42bb766&arch=all&type=main[/HTML] 

Next j2re

> **bored2k]Okay just forget about the Backported Java and build yer own ! It's just as easy.

1. [url]https://sdlcweb2d.sun.com/ECom/EComActionServlet said:**
> 
2.
Download** Linux self-extracting file   	jre-1_5_0_04-linux-i586.bin  	15.83 MB**
3.
sudo apt-get install fakeroot java-package
4.
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
5.
sudo dpkg -i *.deb (whatever the newly Sun- DEBian package is named).

And last i installed azureus.

---

### Post by Unit #134679 on 2005-09-23
Sweet! It worked! Thanks man!

---

