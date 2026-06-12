---
title: "Cannot run thinfeeder, java problem?"
date: 2008-03-30
forum: General Help
---

### Post by TidusBlade on 2008-03-30
Well, I'm trying to run thinfeeder, and I keep getting the same error, dunno whats the cause, but I'm guessing it's Java related?
This is what happens when I run it under my normal user account
```
watermelon@mint:~/Apps/RSS/thinfeeder_1_3_3_LINUX$ bash thinfeeder.sh
Starting ThinFeeder...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading ThinFeeder:
cache_scale: 14
cache_size_scale: 8
writeScript
Cache.saveRow() total row save time in 1 ms.
Cache.saveRow() total row save count = 1
Cache.makeRow() total row load time in 4 ms.
Cache.makeRow() total row load count = 3
Cache.sort() total time in 0 ms.
Database connection created
Error: Couldn't find per display information
ThinFeeder TERMINATED.

```
And this is under root
```

root@mint:/home/watermelon/Apps/RSS/thinfeeder_1_3_3_LINUX# bash thinfeeder.sh
Starting ThinFeeder...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading ThinFeeder:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.font.FontDesignMetrics.getDefaultFrc(FontDesignMetrics.java:135)
        at sun.font.FontDesignMetrics.getMetrics(FontDesignMetrics.java:232)
        at java.awt.Component.getFontMetrics(Component.java:2716)
        at net.sourceforge.thinfeeder.widget.Splash.<init>(Splash.java:61)
        at net.sourceforge.thinfeeder.StartupHandler.open(StartupHandler.java:154)
        at net.sourceforge.thinfeeder.StartupHandler.main(StartupHandler.java:172)
ThinFeeder TERMINATED.

```
I tried this with the Linux version of it.

Any help would he hugely appreciated =]
Thanks!

---

