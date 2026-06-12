---
title: "[SOLVED] Java error on browser"
date: 2008-06-09
forum: General Help
---

### Post by Ahrk on 2008-06-09
Hi, I have been unable to load chatrooms in my browser (I have tried it on firefox 3 beta 5 and epiphany). The chatroom never loads, although I can see the progress bar. I have the java plugin installed and it works fine in pages like youtube. I tried running the browser in the terminal and this is the output I get whenever I go to the chatroom page:

Exception in thread "Thread-3" java.lang.NoClassDefFoundError: netscape/javascript/JSObject
	at SigmaChat.init(Unknown Source)
	at Client.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.ClassNotFoundException: netscape.javascript.JSObject
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at java.net.FactoryURLClassLoader.loadClass(URLClassLoader.java:615)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268 )
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 3 more

I don't know if this has anything to do with the issue, but a while back I wasn't able to run frostwire and used:

sudo update-alternatives --config java

the options were:

         1    /usr/lib/jvm/java-6-sun/jre/bin/java
         2    /usr/bin/gij-4.2
+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

option 3 was set by default but I could only run frostwire by switching to option 1.

Thanks in advance for your help.

---

### Post by jamesstansell on 2008-06-09
netscape/javascript/JSObject is sometimes known as the java bridge, and there is an open bug for icedtea-gcjwebplugin about not supporting it.

Your best option at this time is probably to install the sun-java6-plugin package.```
$ sudo apt-get install sun-java6-plugin
```

I would also make sure that the icedtea-gcjwebplugin package is uninstalled.

---

### Post by Ahrk on 2008-06-09
Thanks James, that worked!

After trying to install the sun-java6-plugin I got a message saying it was already installed. Then I uninstalled the icedtea-gcjwebplugin package using the synaptic package manager and restarted firefox and it could load the pages now.

Thank you very much for your help.

Aaron.:guitar:

---

