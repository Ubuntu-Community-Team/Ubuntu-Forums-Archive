---
title: "Azureus &amp; System Monitor won't start."
date: 2008-01-31
forum: General Help
---

### Post by Deiz on 2008-01-31
When Azureus is run in terminal it spits out:

```
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
[GUI] StartServer ERROR: unable to bind to 127.0.0.1:6880 listening for passed t&#65533;&#65533;&#65533;&#65533;}t info: /usr/lib/jvm/java-7-icedtea/jre/lib/i386/libnet.so: &#65533;&#65533;}&#65533;
ï¿½ï¿½&#9532;ï¿½&#9148;£Uï¿½ï¿½Fï¿½Z£ï¿½ï¿½ï¿½ï¿½A£ï¿½ï¿½ï¿½ï¿½ï¿½(£7&#65533;&#65533;&#65533;&#65533;£ï¿½&#65533;&#65533;&#65533;&#65533;&#65533;|&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;|&#65533;&#65533;b&#65533;|gy&#65533;=&#65533;|&#65533;m&#65533;&#65533;|: cannot open shared object file: No such file or directory
StartSocket: passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class java.net.InetAddress
        at java.net.InetSocketAddress.<init>(InetSocketAddress.java:142)
        at java.net.Socket.<init>(Socket.java:200)
        at org.gudy.azureus2.ui.swt.StartSocket.sendArgs(StartSocket.java:57)
        at org.gudy.azureus2.ui.swt.Main.processParams(Main.java:152)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:74)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)

```

No graphics are loaded; this happens instantaneously upon being run.

With System Monitor, I get:

```
gnome-system-monitor: symbol lookup error: /usr/lib/libpangomm-1.4.so.1: undefined symbol: _ZNK4Glib10ObjectBase9referenceEv

```

This has happened for three or four reboots now. This issue started at the same time that Azureus began have issues.

---

### Post by cozmicharlie on 2008-01-31
It sounds like a Java problem.  What version of Java are you using?  You should be using Sun Java JRE.  There is a neat trick in Ubuntu to check Java versions:

sudo update-alternatives --config java

If you have Sun Java installed make sure that is the one being used and not some weird version.
__________________

---

### Post by Deiz on 2008-01-31
> **cozmicharlie said:**
> It sounds like a Java problem.  What version of Java are you using?  You should be using Sun Java JRE.  There is a neat trick in Ubuntu to check Java versions:

sudo update-alternatives --config java

If you have Sun Java installed make sure that is the one being used and not some weird version.
__________________

That results in:

```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-7-icedtea/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
```

I selected 3, however, only default, *, moves. + does not, and when I fire up Azureus, it still defaults to java-7-icedtea.

---

### Post by cozmicharlie on 2008-01-31
I don't know about the other java versions but I do know that  java6-sun-jre is the one you should use for Azureus.  Not sure why it will not let you default to it though.  Do you have another program open that may be using the icedtea version?  If you don't use the icedtea java you may want to just uninstall it.

---

### Post by cozmicharlie on 2008-01-31
I did a quick search of the forums and it appears that the icedtea java version is causing a lot of problems for people - see this thread for example ([http://ubuntuforums.org/showthread.php?t=680803&highlight=icedtea](http://ubuntuforums.org/showthread.php?t=680803&highlight=icedtea)).

---

### Post by Deiz on 2008-01-31
Great. That appears to be one problem solved - No more trouble with Azureus.

Icedtea is now gone, and Azureus defaulted to Sun's JRE.

However, System Monitor refuses to start, still.

---

### Post by cozmicharlie on 2008-01-31
> **Deiz said:**
> Great. That appears to be one problem solved - No more trouble with Azureus.

Icedtea is now gone, and Azureus defaulted to Sun's JRE.

However, System Monitor refuses to start, still.

Glad I could be of help for at least one of your problems.  Not sure I can help with the system monitor though.  I am not familiar with what the problem could be.  Maybe someone else with more experience in that area can help you.

---

