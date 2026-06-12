---
title: "JAVA Plugin Problem"
date: 2007-10-13
forum: General Help
---

### Post by Vaan on 2007-10-13
Hello, while trying to run the new Azureus (Vuze) it keeps crashing and reports this error when run from the terminal:

> 
(Gecko:16200): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
java: symbol lookup error: /usr/lib/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.


It seems to be some damn error involving "PR.NewMonitor". I've reinstalled JAVA JRE and Azureus multiple times and can't quite figure out what's causing this problem.

Any help?

Thanks.

---

### Post by Tristan Schmelcher on 2007-12-07
I have the same problem. Happens with both Java 5 and 6. Haven't found a fix yet. I don't get the problem when Vuze is off, though, which is the case for my normal user account. But my root user account has Vuze on so it exits shortly after starting, which means I can't download updates. :(

---

### Post by bunkacid on 2008-01-12
I'm having this exact problem with miro. 

/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor

---

### Post by anindya_m on 2008-02-17
Hi. I don't really have a solution, but the problem seems to be related to libnspr, which defines the symbol Pr_NewMonitor in the TEXT segment. The libjavaplugin refers to this symbol. The problem appears after there was an update to libnspr4 so the symbol is not in its original address. So any application which uses the embedded mozilla renderer and tries to open a java-enabled page will have this problem. This is the case for azureus (java app) and miro (python app), for example. So technically it is not a bug with azureus per se.

For some reason, firefox itself seems to run fine with the java plugin!

A workaround is to remove/replace the file libjavaplugin_oji.so, if you like the vuze interface. If you can live with the classic interface, then you can use the ui switcher to set azureus to start up with that interface. This has the advantage of not having to mess with system libraries. Just remember to disable the network before you start azureus for the first time, so that it does not crash while loading the startup page and you get the chance to set the ui. After it is done the network can be enabled.

---

### Post by dcatdemon on 2008-03-13
Found that Sun's JDK/JRE 1.6.0_05 resolves this problem.  

I've tested with 1.6.0_04 and the problem exists, but with release 05, it seems to go away.

Hope this helps.;)

---

