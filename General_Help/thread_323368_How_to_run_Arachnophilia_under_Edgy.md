---
title: "How to run Arachnophilia under Edgy?"
date: 2006-12-22
forum: General Help
---

### Post by johnpipe on 2006-12-22
I have downloaded Arachnophilia 5.3; the java requirement is Java 2 release 1.4 or better runtime engine. If I try to run it under Edgy, I get the following:


```
johnpipe@linus:~/My_Documents/Arachnophilia$ !457
java -jar Arachnophilia.jar 
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.JFrame.<init>(libgcj.so.70)
   at Arachnophilia.Arachnophilia.<init>(Arachnophilia.java:127)
   at Arachnophilia.Arachnophilia.main(Arachnophilia.java:1520)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...6 more
johnpipe@linus:~/My_Documents/Arachnophilia$ 
```

Anyone know if Arachnophilia can run here, and/or what do I have to do to make it work?

Thanks very much,  
Johnpipe

---

### Post by will103 on 2006-12-22
Hi,

I downloaded the jar file to give it a try (I remember this editor from a while back but didn't realise it had been re-written in Java). It launches fine for me. Try installing the Sun Java 1.5 JRE files using the Automatix installer for Ubuntu [http://www.getautomatix.com/](http://www.getautomatix.com/) 

Good luck

will103

---

### Post by johnpipe on 2006-12-25
> **will103 said:**
> Hi,

I downloaded the jar file to give it a try (I remember this editor from a while back but didn't realise it had been re-written in Java). It launches fine for me. Try installing the Sun Java 1.5 JRE files using the Automatix installer for Ubuntu [http://www.getautomatix.com/](http://www.getautomatix.com/) 

Good luck

will103

Thanks for the suggestion, will103. I'm still not quite used to having a working package manager (synaptic), as my daily desktop is RH6.x on another partition; it suddenly occurred to me to look in there and search for java and found the j2re1.4 package that was needed. After installing it Arachnophilia works fine.

Thanks again,

Johnpipe

---

