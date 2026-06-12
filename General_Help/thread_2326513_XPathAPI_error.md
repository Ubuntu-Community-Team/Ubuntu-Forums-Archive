---
title: "XPathAPI error"
date: 2016-06-01
forum: General Help
---

### Post by Fire Raven on 2016-06-01
I wanted to use the application at [https://sourceforge.net/projects/delineate/files/delineate/0.5/](https://sourceforge.net/projects/delineate/files/delineate/0.5/) which is used to convert bitmap images to vector images. This is the result.

```

$ ./delineate.sh 
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/xpath/XPathAPI
    at net.sf.delineate.utility.XPathTool.string(XPathTool.java:68)
    at net.sf.delineate.utility.XPathTool.string(XPathTool.java:110)
    at net.sf.delineate.DelineateApplication.addControlTab(DelineateApplication.java:86)
    at net.sf.delineate.DelineateApplication.<init>(DelineateApplication.java:62)
    at net.sf.delineate.DelineateApplication.main(DelineateApplication.java:316)
Caused by: java.lang.ClassNotFoundException: org.apache.xpath.XPathAPI
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
    ... 5 more

```

It looks like I might need to install some kind of xpath/XPath package, but I can't tell which package(s) would be appropriate.

---

### Post by codecop on 2017-02-12
Same error...

---

