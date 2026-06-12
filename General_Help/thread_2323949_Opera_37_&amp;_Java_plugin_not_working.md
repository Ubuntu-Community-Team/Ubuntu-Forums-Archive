---
title: "Opera 37 &amp; Java plugin not working"
date: 2016-05-09
forum: General Help
---

### Post by michaelbr on 2016-05-09
Hi:
I have Ubuntu 14.04, Opera 37 and openJDK installed and working, but when I had installed Eclipse with Python, I had to install Oracle Java 8 and was told that I had to remove IcedTea, and openJDK, now my Java plugin does not work any longer, what should I do to enable it?

The Oracle Java is installed, in terminal when I type
```
$ java -version
java version "1.8.0_91"
Java(TM) SE Runtime Environment (build 1.8.0_91-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.91-b14, mixed mode)
```
so I believe Java is installed, but why Opera can't see it? I tried to search web with no luck. Can someone please direct me to the right place how to solve this problem? Thanks for your comment/suggestion.

---

### Post by CantankRus on 2016-05-09
Opera is based on webkit and chromium as is google-chrome. I believe support was dropped for NPAPI 
which the java plugin requires. 
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("https://www.java.com/en/download/faq/chrome.xml")

The java plugin is still recognized in Firefox.

---

### Post by michaelbr on 2016-05-10
> **CantankRus said:**
> Opera is based on webkit and chromium as is google-chrome. I believe support was dropped for NPAPI 
which the java plugin requires. 
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("https://www.java.com/en/download/faq/chrome.xml")

The java plugin is still recognized in Firefox.

Thanks CantankRus for your reply, I thought it was something I missed.

---

