---
title: "No MANIFEST.MF in JabRef.jar"
date: 2005-06-21
forum: General Help
---

### Post by Daan on 2005-06-21
Hi all,

Nice forums these are, they have helped me install some programs that were not easy to install. I'm new to Linux and Ubuntu, so help is really appreciated.

Now, I cannot find any good help on the following. When I try to install a program called JabRef, following the steps given at [http://jabref.sourceforge.net/installation.html](http://jabref.sourceforge.net/installation.html) . I get stuck at the last step:

```
...$ java -jar JabRef.jar
Error: No MANIFEST.MF or Main-Class: in MANIFEST.MF found in JabRef.jar
```

What can I do?

---

### Post by Daan on 2005-06-22
OK. So I've made a silly mistake. The JabRef.jar file mentioned in the installation instructions at sourceforge  does not exsist, in stead there's a .jar file that has a version number in its name:

```
...$ java -jar JabRef-1.8b.jar
```

Doing that, I still got a lot of errors:

```
java.lang.ClassNotFoundException: javax.swing.plaf.metal.MetalBorders$ScrollPaneBorder not found in [file:/home/daan/pack/JabRef-1.8b.jar, file:/usr/share/java/gnujaxp.jar, file:/home/daan/pack/./]
   at java.net.URLClassLoader.findClass (URLClassLoader.java:748)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:359)
   at java.lang.ClassLoader$1.loadClass (ClassLoader.java:1282)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:303)
   at java.lang.VirtualMachine.createClass (VirtualMachine.java:100)
   at java.lang.VMClassLoader.nativeDefineClass (VMClassLoader.java)
   at java.lang.VMClassLoader.defineClass (VMClassLoader.java:96)
   at java.lang.ClassLoader.defineClass (ClassLoader.java:672)
   at java.security.SecureClassLoader.defineClass (SecureClassLoader.java:88)
   at java.net.URLClassLoader.findClass (URLClassLoader.java:833)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:359)
   at java.lang.ClassLoader$1.loadClass (ClassLoader.java:1282)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:303)
   at java.lang.VirtualMachine.createClass (VirtualMachine.java:100)
   at com.jgoodies.plaf.plastic.PlasticBorders.getScrollPaneBorder (PlasticBorders.java:262)
   at com.jgoodies.plaf.plastic.PlasticLookAndFeel.initComponentDefaults (PlasticLookAndFeel.java:299)
   at com.jgoodies.plaf.plastic.Plastic3DLookAndFeel.initComponentDefaults (Plastic3DLookAndFeel.java:74)
   at javax.swing.plaf.basic.BasicLookAndFeel.getDefaults (BasicLookAndFeel.java:92)
   at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults (MetalLookAndFeel.java:89)
   at javax.swing.UIManager.put (UIManager.java:414)
   at net.sf.jabref.JabRef.main (JabRef.java:513)
   at java.lang.VirtualMachine.invokeMain (VirtualMachine.java)
   at java.lang.VirtualMachine.main (VirtualMachine.java:92)
Trying to set system default Look&Feel...
java.lang.NullPointerException
   at net.sf.jabref.groups.GroupsTree.GroupsTree (GroupsTree.java:67)
   at net.sf.jabref.groups.GroupSelector.GroupSelector (GroupSelector.java:332)
   at net.sf.jabref.JabRefFrame.init (JabRefFrame.java:380)
   at net.sf.jabref.JabRefFrame.JabRefFrame (JabRefFrame.java:336)
   at net.sf.jabref.JabRef.main (JabRef.java:566)
   at java.lang.VirtualMachine.invokeMain (VirtualMachine.java)
   at java.lang.VirtualMachine.main (VirtualMachine.java:92)
```

Using a the latest version that is not beta, I got less errors (not the NullPointerException in the above code). And I did get a running JabRef.
```

...$ java -jar JabRef-1.7.1.jar
```

However, this running JabRef still gives many errors and cannot be used... :-(

---

