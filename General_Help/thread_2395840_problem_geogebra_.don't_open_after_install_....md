---
title: "problem geogebra .don't open after install ..."
date: 2018-07-07
forum: General Help
---

### Post by dimzev on 2018-07-07
I install Geogebra from software center in Ubuntu 18.04 (gnome) and Kubuntu 18.04 (KDE) .
I have the same problem….
 Don’t open  …
 When write the terminal “geogebra” I take :
 
 
 > GeoGebra 4.0.34.0 (Debian version 4.0.34.0+dfsg1-4) 22 June 2012 Java 10.0.1

 *** Message from [geogebra.main.Application.setUpLogging]

         /tmp/GeoGebraLog_rydoyjbrop.txt

 
 
 and the text to tmp write:
 
 
 
 
 > Jul 07, 2018 6:32:33 PM   

 STDOUT:   current views:
 
 
 Jul 07, 2018 6:32:33 PM   
 STDOUT: geogebra.euclidian.EuclidianView[,0,0,0x0,invalid,alignmentX=0.0,alignmentY=0.0,border=,flags=9,maximumSize=,minimumSize=java.awt.Dimension[width=20,height=20],preferredSize=]
 
 
 Jul 07, 2018 6:32:33 PM   
 STDERR: XXXXXXXXX Number of registered views = 1
 Jul 07, 2018 6:32:33 PM   
 STDOUT: class geogebra.euclidian.EuclidianView
 Jul 07, 2018 6:32:33 PM   
 STDERR: *** Message from [geogebra.gui.view.algebra.AlgebraView.<init>]
 Jul 07, 2018 6:32:33 PM   
 STDERR:  
 Jul 07, 2018 6:32:33 PM   
 STDERR: XXX creating Algebra View XXX
 Jul 07, 2018 6:32:34 PM   
 STDOUT:   current views:
 
 
 Jul 07, 2018 6:32:34 PM   
 STDOUT: geogebra.euclidian.EuclidianView[,0,0,0x0,invalid,alignmentX=0.0,alignmentY=0.0,border=,flags=9,maximumSize=,minimumSize=java.awt.Dimension[width=20,height=20],preferredSize=java.awt.Dimension[width=640,height=480]]
 
 
 Jul 07, 2018 6:32:34 PM   
 STDOUT: geogebra.gui.view.algebra.AlgebraView[,0,0,0x0,invalid,alignmentX=0.0,alignmentY=0.0,border=javax.swing.border.EmptyBorder@43b4fe19,flags=16777576,maximumSize=,minimumSize=,preferredSize=,editable=true,invokesStopCellEditing=true,largeModel=true,rootVisible=false,rowHeight=-1,scrollsOnExpand=true,showsRootHandles=false,toggleClickCount=1,visibleRowCount=20]
 
 
 Jul 07, 2018 6:32:34 PM   
 STDERR: XXXXXXXXX Number of registered views = 2
 Jul 07, 2018 6:32:34 PM   
 STDOUT: class geogebra.euclidian.EuclidianView
 Jul 07, 2018 6:32:34 PM   
 STDOUT: class geogebra.gui.view.algebra.AlgebraView
 Jul 07, 2018 6:32:34 PM   
 STDOUT: *** Message from [geogebra.main.GeoGebraPreferences.loadPrefsSystem]
 Jul 07, 2018 6:32:34 PM   
 STDOUT:  
 Jul 07, 2018 6:32:34 PM   
 STDOUT: system preference /geogebra does not exist
 Jul 07, 2018 6:32:34 PM   
 STDOUT: *** Message from [geogebra.main.GeoGebraPreferences.loadVersionCheckAllow]
 Jul 07, 2018 6:32:34 PM   
 STDOUT:  
 Jul 07, 2018 6:32:34 PM   
 STDOUT: no ggbPrefsSystem : systemAllows = true
 Jul 07, 2018 6:32:34 PM   
 STDOUT: *** Message from [geogebra.main.Application.setVersionCheckAllowed]
 Jul 07, 2018 6:32:34 PM   
 STDOUT:  
 Jul 07, 2018 6:32:34 PM   
 STDOUT: versionCheckAllowed = true
 Jul 07, 2018 6:32:34 PM   
 STDERR: java.lang.ClassCastException: java.base/jdk.internal.loader.ClassLoaders$AppClassLoader cannot be cast to java.base/java.net.URLClassLoader
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.plugin.ClassPathManipulator.addURL(ClassPathManipulator.java:68)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.plugin.PluginManager.<init>(PluginManager.java:80)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.main.Application.getPluginManager(Application.java:5048)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.main.Application.<init>(Application.java:612)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.main.Application.<init>(Application.java:467)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.gui.app.GeoGebraFrame.createApplication(GeoGebraFrame.java:288)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.gui.app.GeoGebraFrame.createNewWindow(GeoGebraFrame.java:311)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.gui.app.GeoGebraFrame.createNewWindow(GeoGebraFrame.java:276)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.gui.app.GeoGebraFrame.init(GeoGebraFrame.java:242)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.gui.app.GeoGebraFrame.main(GeoGebraFrame.java:196)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.GeoGebra.startGeoGebra(GeoGebra.java:103)
 Jul 07, 2018 6:32:34 PM   
 STDERR:         at geogebra.GeoGebra.main(GeoGebra.java:88)
 
 
 
 
 what should I do to solve my problem?

 Can anyone help me ?
 The geogebra tool is very important for my job
 
 
 thank you for your time and sorry for my poor English

---

### Post by mc4man on 2018-07-07
It's a bug that probably will not get fixed
[https://bugs.launchpad.net/ubuntu/+source/geogebra/+bug/1775244](https://bugs.launchpad.net/ubuntu/+source/geogebra/+bug/1775244)

Comments suggest trying an upstream package instead (link in  #3

---

