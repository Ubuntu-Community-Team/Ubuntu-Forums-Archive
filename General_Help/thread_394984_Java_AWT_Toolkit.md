---
title: "Java AWT Toolkit"
date: 2007-03-27
forum: General Help
---

### Post by georgecm3 on 2007-03-27
Hello everyone,

I installed the latest Java Runtime Environment, but when I tried to run a java application, Freecol, I got a few erors.
```
george@george-desktop:~/Games/freecol$ java -Xmx256M -jar FreeCol.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.EventQueue.invokeLater(libgcj.so.7)
   at javax.swing.SwingUtilities.invokeLater(libgcj.so.7)
   at net.sf.freecol.FreeCol.main(FreeCol.java:180)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...3 more

```

does anyone know how I can fix this?
Thanks

---

### Post by jordanmthomas on 2007-03-27
Look up how to install Sun's Java.  You're using gcj which is, quite frankly, not so compatible with much.

---

### Post by georgecm3 on 2007-03-27
I think I installed Sun's Java before I had this problem. It's the one from their website right?

---

### Post by jordanmthomas on 2007-03-27
Yes, that's the right one.  You still appear to be using gcj though.
```
java -version
```should output something like this:
```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

I don't think yours will output this.

If you did install it properly, you can run 
```
sudo update-alternatives --config java
```
to select the correct java to use.  I'm not sure which one you need as I don't use Ubuntu and I'm not sure where it goes.  In my Arch installation, it's /opt/java/bin/java.  If you use javac, you'll need to do the same for it.

Otherwise, have a look at installing this package from the Ubuntu repositories:
```
sudo apt-get install sun-java5-bin
```

(you need multiverse repositories activated)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

