---
title: "java applet error in firefox &amp; opera for plugin"
date: 2006-12-04
forum: General Help
---

### Post by defender110 on 2006-12-04
Trying to get a stockchart applet to load. It starts then bombs out with the follwing message in the java console. Can anyone interpret to see what the fix might be?

****************
Java Plug-in 1.5.0_08
Using JRE version 1.5.0_08 Java HotSpot(TM) Client VM
User home directory = /home/jam


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

finance.lycos.com LiveCharts (012004 PularAds) (C)1998,1999,2000,2001,2002,2003,2004 TerraLycos, Inc.
URL = [http://www.quote.com/qc/livecharts/ot_timedout.html](http://www.quote.com/qc/livecharts/ot_timedout.html) time= 180000
java.lang.NullPointerException
	at sun.awt.X11.XMenuPeer.repaintMenuItem(XMenuPeer.java:363)
	at sun.awt.X11.XCheckboxMenuItemPeer.setState(XCheckboxMenuItemPeer.java:46)
	at java.awt.CheckboxMenuItem.setState(CheckboxMenuItem.java:177)
	at livecharts.LiveChartsV3.initForm(LiveChartsV3.java:2158)
	at livecharts.LiveChartsV3.init(LiveChartsV3.java:1006)
	at sun.applet.AppletPanel.run(AppletPanel.java:378)
	at java.lang.Thread.run(Thread.java:595)
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring
**********************************

Thanks,

---

