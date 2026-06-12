---
title: "Eclipse Crashing"
date: 2006-11-10
forum: General Help
---

### Post by marcog on 2006-11-10
Eclipse is crashing on me. I'm running Edgy on a Core 2 Duo. This is what appears in the log file:

```
!SESSION 2006-11-10 23:30:22.535 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_ZA
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2006-11-10 23:30:27.597
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
   at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
   at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```

---

### Post by marcog on 2006-11-12
Anyone?

---

### Post by ewel on 2006-11-12
I had installed eclipse using apt-get -> same problem, so i removed it and downloaded eclipse from www:
[http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/index.php](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/index.php)
(Linux (x86_64/GTK 2) version), and next installed sun-j2re1.5_1.5.0+update09_amd64.deb  (probably from java.sun.com. I'm not sure, I found it on my hard disk  :) )
then unpack eclipse-SDK-3.2.1-linux-gtk-x86_64.tar.gz, and run ./eclipse from  /home/user/eclipse directory and now it's ok

---

### Post by jordilin on 2006-11-12
> **marcog said:**
> Eclipse is crashing on me. I'm running Edgy on a Core 2 Duo. This is what appears in the log file:

```
!SESSION 2006-11-10 23:30:22.535 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_ZA
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-10 23:30:27.140
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2006-11-10 23:30:27.597
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
   at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
   at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```
Which version of java are you running?
Type 
```
$sudo update-alternatives --config java
```
and tell us. For best performance, you should install the Sun Microsystems Java. Take a look here:
[http://jordilin.wordpress.com/2005/11/23/installing-java-in-ubuntu/](http://jordilin.wordpress.com/2005/11/23/installing-java-in-ubuntu/)

---

### Post by marcog on 2006-11-13
> **ewel said:**
> I had installed eclipse using apt-get -> same problem, so i removed it and downloaded eclipse from www:
[http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/index.php](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/index.php)
(Linux (x86_64/GTK 2) version), and next installed sun-j2re1.5_1.5.0+update09_amd64.deb  (probably from java.sun.com. I'm not sure, I found it on my hard disk  :) )
then unpack eclipse-SDK-3.2.1-linux-gtk-x86_64.tar.gz, and run ./eclipse from  /home/user/eclipse directory and now it's ok

Installing the version from the eclipse site and it works. Thanks! :)

---

### Post by jlapier on 2006-11-16
ditto - 6.10 on amd64, had to use package from eclipse.org, the one in the repo was crashing with the same output you guys posted.

---

### Post by marcog on 2006-11-18
Is there anything that is being done to fix the packages in the reop? Going through the reops is just much easier for new users. And eclipse is a fairly important application to be bogged down by an error this bad.

---

### Post by hk_2999 on 2006-11-19
True. I'm having this prob too. The bug's already posted, and a fix had been proposed. But I don't know when they will ever take action for this. 

[https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/68053](https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/68053)

Anyway, if ever someone can make a temporary deb fix can someone post it here?

---

### Post by paradroid on 2006-11-19
[COLOR="DarkGreen"]**download eclipse amd 64 version**[/COLOR] from eclipse.org: [http://www.eclipse.org/downloads/]("http://www.eclipse.org/downloads/") 

[COLOR="DarkGreen"]**unpack to local folder** ~/apps[/COLOR].

then create a menu item:

[COLOR="DarkGreen"]**right click at 'K Menu'** >> **choose 'Menu Editor'** >> **create new item** wherever you want >> program name is **~/apps/eclipse/eclipse** >> **Run as diffrent user**: [yourself] >> Don't forget to SAVE ...[/COLOR]

... and have fun :cool: cheers !

---

### Post by hk_2999 on 2006-11-19
thanks, i've been using that solution since the day eclipse got broke but maybe some other users might use that knowledge. :)

---

