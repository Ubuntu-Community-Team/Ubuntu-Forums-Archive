---
title: "GTK/Java trouble"
date: 2007-05-21
forum: General Help
---

### Post by DaOane on 2007-05-21
I try to make FinchSync work on my Ubuntu 7.04 system. After an upgrade to Sun Java 1.6 the application starts now, but the application window is an empty GTK window with just the background (if not, all subsequent windows are empty). If I run the application with the following command:

java -verbose -jar FinchSync.jar | grep Error 

I get in return

> [Loaded java.lang.Error from shared objects file]
[Loaded java.lang.LinkageError from shared objects file]
[Loaded java.lang.NoClassDefFoundError from shared objects file]
[Loaded java.lang.VirtualMachineError from shared objects file]
[Loaded java.lang.OutOfMemoryError from shared objects file]
[Loaded java.lang.StackOverflowError from shared objects file]
[Loaded java.lang.IncompatibleClassChangeError from shared objects file]
[Loaded java.lang.NoSuchMethodError from shared objects file]
[Loaded java.nio.charset.CodingErrorAction from shared objects file]
[Loaded sun.awt.X11.XToolkit$XErrorHandler from shared objects file]
[Loaded sun.awt.X11.XErrorEvent from shared objects file]
[Loaded org.apache.log4j.spi.ErrorHandler from file:/home/hl/Desktop/FinchSync/FinchSync.jar]
[Loaded org.apache.log4j.helpers.OnlyOnceErrorHandler from file:/home/hl/Desktop/FinchSync/FinchSync.jar]
[Loaded org.xml.sax.ErrorHandler from shared objects file]
[Loaded com.sun.org.apache.xerces.internal.impl.XMLErrorReporter from /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/rt.jar]
[Loaded com.sun.org.apache.xerces.internal.xni.parser.XMLErrorHandler from /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/rt.jar]
[Loaded com.sun.org.apache.xerces.internal.util.ErrorHandlerWrapper from /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/rt.jar]
[Loaded javax.xml.transform.ErrorListener from /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/rt.jar]


I posted this as well on the [FinchSync forum]("http://www.finchsync.com/forums/viewtopic.php?t=735") but without sucess. Does anybody know what is wrong or how I can obtain more information about the problem? Thanks,

Henning

---

### Post by Psicolonia on 2007-05-21
disable desktop effects. and restart your application.

---

### Post by DaOane on 2007-05-22
Great! Thanks! Now it works ...  it's just to hope that Desktop Effects become completely compatible with Java or/and GTK (whatever the problem is) in the future!

=> It's necessary to turn off Desktop Effects for the server/client setup only. The daily use, i.e. synchronization with FinchSync, works fine with Desktop Effects enabled.

---

### Post by jazzypants on 2007-05-27
this seems to be a common theme with GTK/Java apps in Gnome...

that being said, i do not have Desktop Effects installed on my machine per se, but i do have Beryl installed so i assume i'm facing the same issue.  after fiddling with the Beryl settings, i was able to handle this issue.  so, for those of us out there that have a Beryl installation, here's what you can do to handle this:

in the Beryl manager, change the window manager from Beryl (or Compiz) back to Metacity.  then, you should be able to run any GTK/Java app.  a pain in the **** perhaps, but at least it will allow you to see more than that stupid blank window.  then, just switch back to your window manager of choice when you are done.

enjoy!

---

### Post by macabro22 on 2007-05-30
Isn't there a more sensible solution to this? I don't wanna have to turn off beryl. If I do so, awn wont work properly.

---

### Post by Psicolonia on 2007-05-30
you can put your java applications inside VirtualBox. :p

I'm joking... i don't think there is, it's a known bug though...

i've got metacity activated and it's the same thing... i don't think that's the issue...

---

### Post by henryContreras on 2007-08-04
If you don't want to restart beryl there is a solution:
[http://bok.cronicando.com/blank-window-on-java-applications-under-beryl/]("http://bok.cronicando.com/blank-window-on-java-applications-under-beryl/")

If that does not work you can try typing that command (export AWT_TOOLKIT=MToolkit) in a console and lauch your application from the same console.

---

