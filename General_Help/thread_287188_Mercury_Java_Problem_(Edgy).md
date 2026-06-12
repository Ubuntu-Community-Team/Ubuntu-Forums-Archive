---
title: "Mercury Java Problem (Edgy)"
date: 2006-10-28
forum: General Help
---

### Post by Skootle on 2006-10-28
Hi. I downloaded Mercury (**not** via aptitude) but when I type "Mercury" in the console, it doesn't start and I get the following error:

```
Exception in thread "main" java.lang.NoClassDefFoundError: com/dMSN/Main

```

When I type "sudo update-alternatives --config java", I get the following output:

```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

I have already installed Java 1.5 JRE [via Automatix2](http://img48.imageshack.us/img48/9269/screenshotvw3.png).

Any ideas on how to fix the problem? Thanks. :)

---

