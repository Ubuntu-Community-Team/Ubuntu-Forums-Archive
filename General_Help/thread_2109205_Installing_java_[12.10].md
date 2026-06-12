---
title: "Installing java? [12.10]"
date: 2013-01-26
forum: General Help
---

### Post by tahdas on 2013-01-26
How do i install java on Ubuntu 12.10? 

Thanks,
tahdas

---

### Post by ntzrmtthihu777 on 2013-01-26
This did the trick for me:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
Hope it helps, if it does mark the thread as [SOLVED]

---

### Post by mattyasaurus on 2013-01-27
> **tahdas said:**
> How do i install java on Ubuntu 12.10? 

Thanks,
tahdas

To install Oracle Java 7 in Ubuntu 12.10 use the following commands in Terminal:
```
**sudo add-apt-repository ppa:webupd8team/java** 
**sudo apt-get update** 
**sudo apt-get install oracle-java7-installer**
```

If you ever want to remove Oracle Java 7 from your system at any point run the following command in Terminal:
```
**sudo apt-get remove oracle-java7-installer**
```

---

### Post by Spyderkid on 2013-01-27
Just install ubuntu restricted extras from the software center, should have all the stuff you needfor java and other general things.

Also chromium/Google Chrome comes with java built in i believe

---

