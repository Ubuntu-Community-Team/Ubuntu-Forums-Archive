---
title: "Citrix access Java problem"
date: 2008-01-28
forum: General Help
---

### Post by v4169sgr on 2008-01-28
Ubuntu 6.06 on 32-bit x86. 2.6.15-51-k7 #1 SMP PREEMPT

Citrix ICA Client for Linux
Version 10.6.115659
Copyright (c) 1998-2007 Citrix Systems, Inc. All rights reserved.
Copyright (c) 1986-1997 RSA Security, Inc. All rights reserved.

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Server VM (build 1.5.0_06-b05, mixed mode)

Attempting to connect to work from home using Firefox 1.5.0.13pre:

- SecurID authentication - OK;

- Wndows Logon - OK;

- Pop up window launching Ctrix client - OK

Then have error message 'Loading Java Applet Failed ...'.

Full error message is

```
Java Plug-in 1.5.0_06
Using JRE version 1.5.0_06 Java HotSpot(TM) Client VM
User home directory = /home/andrew


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

java.lang.ClassFormatError: Incompatible magic value 171731060 in class file com/citrix/JICA
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:163)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:119)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:591)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:721)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1757)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:650)
	at sun.applet.AppletPanel.run(AppletPanel.java:324)
	at java.lang.Thread.run(Thread.java:595)

```

Followed directions in this thread: [http://ubuntuforums.org/showthread.php?t=510965](http://ubuntuforums.org/showthread.php?t=510965) but have the 'right' Java installed and preferred.

Work have given the 'DO NOT SUPPORT' message, so I'm on my own.

Any ideas folks?

---

### Post by v4169sgr on 2008-01-29
*bump* Any ideas?

---

