---
title: "About Java Runtime Environment plugin"
date: 2008-06-16
forum: General Help
---

### Post by satimis on 2008-06-16
Hi folks,


Ubuntu server 7.04 amd64
Firefox


I need "Java Runtime Environment plugin' visiting some websites.  I have the self-extract package jre-6u6-linux-x64.bin download and installed on

/usr/java/jre1.6.0_06/bin/


Please advise how to make it to work.  TIA


Edit --> Preference --> Content --> Enable Java
already check


B.R.
satimis

---

### Post by jespdj on 2008-06-16
You are using a 64-bit version of Ubuntu. There is, unfortunately, no 64-bit browser plugin for Sun Java. (The 64-bit version of Java from Sun simply does not include a browser plugin). So you can't use Sun Java for this.

You could try using OpenJDK or IcedTea Java, but I'm not sure if those are available for Ubuntu 7.04.

Otherwise, you could install a 32-bit browser and a 32-bit version of Java. You can find more info on how to do that in [this thread](http://ubuntuforums.org/showthread.php?t=202537).

---

### Post by Sef on 2008-06-16
> You could try using OpenJDK or IcedTea Java, but I'm not sure if those are available for Ubuntu 7.04.

I believe they are in the repositories.

Applications > Add/Remove > Search: OpenJDK

---

### Post by satimis on 2008-06-16
> **Sef said:**
> I believe they are in the repositories.

Applications > Add/Remove > Search: OpenJDK
Thanks for your advice.


$ apt-cache policy openjdk
No printout


$ apt-cache search jdk | grep open
can't find it.


B.R.
satimis

---

### Post by Sinkingships7 on 2008-06-16
This will solve your Java issues:
```
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by Nepherte on 2008-06-16
> **Sinkingships7 said:**
> This will solve your Java issues:
```
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
No it won't, there's no sun-java6-plugin package for 64bit.

This package is available for gutsy, try:
```
sudo apt-get install icedtea-java7-plugin
```

---

### Post by Sinkingships7 on 2008-06-16
> **Nepherte said:**
> No it won't, there's no sun-java6-plugin package for 64bit.

This package is available for gutsy, try:
```
sudo apt-get install icedtea-java7-plugin
```

Got me there. :lolflag:

---

### Post by satimis on 2008-06-16
Hi folks,


Thanks for your advice.


I'm running Ubuntu 7.04 feisty.  I can't find icedtea-java7-plugin on repo.  I found this package on;

[http://packages.ubuntu.com/search?searchon=names&keywords=icedtea](http://packages.ubuntu.com/search?searchon=names&keywords=icedtea)

It is on gusty and hardy repo.  Which one shall I download.  TIA


B.R.
satimis

---

### Post by avtolle on 2008-06-16
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) Please take a look at this, as you are running 7.04.

---

