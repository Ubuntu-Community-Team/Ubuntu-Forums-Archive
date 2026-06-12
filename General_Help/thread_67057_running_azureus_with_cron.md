---
title: "running azureus with cron"
date: 2005-09-19
forum: General Help
---

### Post by wellery on 2005-09-19
I'm trying to setup azureus so that it runs as a cron job. I keep getting an error in the mail for the job.

This is what I'm doing.

 ```
home@home:~$ crontab
``` 

Then edit the file so it looks like this:

 ```
SHELL=/bin/sh
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

35 21 * * 1	 /usr/bin/azureus %U

``` 


Then the error is:

 ```
Exception in thread "main" org.eclipse.swt.SWTError: No more handles
		at org.eclipse.swt.SWT.error(SWT.java:2853)
		at org.eclipse.swt.SWT.error(SWT.java:2752)
		at org.eclipse.swt.SWT.error(SWT.java:2723)
		at org.eclipse.swt.widgets.Display.createDisplay(Display.java:717)
		at org.eclipse.swt.widgets.Display.create(Display.java:706)
		at org.eclipse.swt.graphics.Device.<init>(Device.java:123)
		at org.eclipse.swt.widgets.Display.<init>(Display.java:412)
		at org.eclipse.swt.widgets.Display.<init>(Display.java:40:cool:
		at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:77)
		at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:5:cool:
		at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:107)
		at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:71)
		at org.gudy.azureus2.ui.swt.Main.main(Main.java:9:cool:

```

---

### Post by lithorus on 2005-09-19
You should try and look into how you run azureus from command line :
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

---

### Post by hacksaw on 2007-02-10
Because cron runs a new shell it won't know which X display to connect to, so try this.

```
gogogo:~$ crontab -e
```

```
35 21 * * 1 xterm -display :0 -e /usr/bin/azureus
```

---

