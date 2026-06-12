---
title: "Start Azureus through SSH"
date: 2007-01-19
forum: General Help
---

### Post by lassegs on 2007-01-19
Hi

I have a server/desktop-computer (with X) running Azureus and SSH. Lets call this computer 10.0.0.5

I want to be able to start up Azureus via SSH from another computer, lets call it 10.0.0.8, on 10.0.0.5's X, so that Azureus runs on the desktop of 10.0.0.5.

From 10.0.0.8 I start an SSH session to 10.0.0.5, then I log inn, then what do i do?

Cheers
Lasse
```
lasse@cyan:~$ /opt/azureus/azureus 
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" org.eclipse.swt.SWTError: No more handles [gtk_init_check() failed]
        at org.eclipse.swt.SWT.error(SWT.java:3400)
        at org.eclipse.swt.widgets.Display.createDisplay(Display.java:793)
        at org.eclipse.swt.widgets.Display.create(Display.java:781)
        at org.eclipse.swt.graphics.Device.<init>(Device.java:145)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:452)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:443)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:91)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:107)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)
Azureus TERMINATED.

```

---

### Post by lassegs on 2007-01-19
Ah, after some more googling, i found out for my self! Yay for me! 

[http://www.linuxquestions.org/questions/showthread.php?t=490426](http://www.linuxquestions.org/questions/showthread.php?t=490426)

> 
Assuming you want to launch something over xine, or under xine (while xine is in fullscreen mode) you could just attach and set the env variable, but you'll need to run xhost + as the user running the original x session (to allow remote connections). Then:
ssh -l whoever machineb
export DISPLAY=:0
kwrite funnyfile.txt

That did the trick.

Have a nice day.
Lasse

---

