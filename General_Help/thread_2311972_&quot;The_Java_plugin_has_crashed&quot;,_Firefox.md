---
title: "&quot;The Java plugin has crashed&quot;, Firefox"
date: 2016-01-31
forum: General Help
---

### Post by starrtennis on 2016-01-31
[https://drive.google.com/file/d/0B_IKPFVu1eF8YTkxVnQzVzY2aWc/view?usp=sharing](https://drive.google.com/file/d/0B_IKPFVu1eF8YTkxVnQzVzY2aWc/view?usp=sharing)

The java detection thing on Java's website yields the error in the title.

I have the latest version of java installed, and i created a symbolic link in the fire fox plugins directory. Firefox detects the plugin.

Oracle's support is absolutely atrocious. This is the most popular frippin video plugin in the world, and it has routinely not worked for me in the past and present. Really peeved.

Thank you for your help.

---

### Post by QIII on 2016-01-31
If you had to create a symbolic link, then you have not installed Java using the easiest method.  (I'm assuming here that you are not talking about OpenJDK, since that can be installed from the repositories.  OpenJDK, by the way, is the open source reference implementation of Oracle Java -- that is to say that Oracle has decreed that all things "Java" must comply with OpenJDK.  If you install it and the IcedTea plugin, you will find that the Java test page will say you have Java installed.)

To install Oracle Java, please see [this]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

Andrew maintains some of the very few PPAs I will use.

---

### Post by starrtennis on 2016-01-31
> **QIII said:**
> If you had to create a symbolic link, then you have not installed Java using the easiest method.  (I'm assuming here that you are not talking about OpenJDK, since that can be installed from the repositories.  OpenJDK, by the way, is the open source reference implementation of Oracle Java -- that is to say that Oracle has decreed that all things "Java" must comply with OpenJDK.  If you install it and the IcedTea plugin, you will find that the Java test page will say you have Java installed.)

To install Oracle Java, please see [this]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

Andrew maintains some of the very few PPAs I will use.

Thank you so much! It worked like a charm. I didn't install the IcedTea plugin, not sure how to. But it works without it.

---

