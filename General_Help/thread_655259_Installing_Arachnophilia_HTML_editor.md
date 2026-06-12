---
title: "Installing Arachnophilia HTML editor"
date: 2008-01-01
forum: General Help
---

### Post by reler on 2008-01-01
Complete Linux newb here. I am trying to get the Arachnophilia HTML editor going. The instructions at [http://www.arachnoid.com/arachnophilia/index.html](http://www.arachnoid.com/arachnophilia/index.html) say[INDENT]Open a command console (Linux: shell console), move to the Arachnophilia program directory, type "java -jar Arachnophilia.jar" [/INDENT]
This is what I get:[INDENT]Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at Arachnophilia.Arachnophilia.<init>(Unknown Source)
   at Arachnophilia.Arachnophilia.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more
[/INDENT]
:?:

I guess something is missing ... can anybody suggest the next step please ?

Thanks.

Reler

PS: Happy New Year !

---

### Post by timboellis on 2008-01-01
Well I have just done a new install of Ubuntu downloaded the Java 6 runtimes from the add/remove repositories, I then downloaded the application you aretrying to run to my desktop then right clicked and open with Java Runtime 6 and it works

---

### Post by reler on 2008-01-01
OK, that works ! So much for following the instructions on the vendor's web page !

> **timboellis said:**
>  I then downloaded the application you aretrying to run to my desktop then right clicked and open with Java Runtime 6 and it works

Just to clarify this for anybody finding this afterwards, "the application" is the aracnophilia.jar file. As timboellis says, if you have a java run time environment (like Sun), when you right-click you will have the option to start with that.

Again, can't believe it was that easy when I thought that I was doing the right thing by following the instructions !

Thanks timboellis.

Reler

---

### Post by timboellis on 2008-01-01
No problem happy to help, I am a newbie so came across this yesterday

---

