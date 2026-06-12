---
title: "Frostwire can't start due to crash java"
date: 2008-03-22
forum: General Help
---

### Post by YSH on 2008-03-22
When i start up frostwire (limewire-clone) it comes with an error about java: 
 An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ade38f04e25, pid=21010, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid21010.log

other programms also requiring java (openoffice) do run just fine. What can i do about this?

---

### Post by YSH on 2008-03-22
i just started it directly, and then it only shows a popup:
FrostWire version @version@
Java version 1.6.0_03 from Sun Microsystems Inc.
Linux v. 2.6.22-14-generic on amd64
Free/total memory: 18386792/29687808

com.limegroup.gnutella.gui.GUILoader$StartupFailedException: invalid themes.jar
	at com.limegroup.gnutella.gui.GUILoader.sanityCheck(GUILoader.java:279)
	at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:51)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Main.java:44)

STARTUP ERROR!

after which come al the files in my home directory

---

