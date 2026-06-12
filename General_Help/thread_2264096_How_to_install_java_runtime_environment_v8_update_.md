---
title: "How to install java runtime environment v8 update 31"
date: 2015-02-05
forum: General Help
---

### Post by mandarpowale on 2015-02-05
I have downloaded and extracted the "jre-8u31-linux-x64.tar.gz" file from jre's download page but i don't know how to run it. Can anyone please help?

If you need any info let me know.

---

### Post by QIII on 2015-02-05
Please don't do it that way.

The very easiest way to install Oracle Java 8 on Ubuntu can be found [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

This automates the download from Oracle, installs Java and sets it as your alternative.  It also is updated when Oracle puts out an update, so you don't have to reinstall Oracle Java every time.

---

### Post by mandarpowale on 2015-02-05
> **QIII said:**
> Please don't do it that way.

The very easiest way to install Oracle Java 8 on Ubuntu can be found [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

This automates the download from Oracle, installs Java and sets it as your alternative.  It also is updated when Oracle puts out an update, so you don't have to reinstall Oracle Java every time.


Thanks a load , I will try that out

It is working. Thanks again.

---

### Post by mandarpowale on 2015-04-13
It was working, but now sudo apt-get install oracle-java8-installer command generates the following error.[ATTACH=CONFIG]261258[/ATTACH]

---

### Post by Vladlenin5000 on 2015-04-13
If it was working why did you tried to install it again?
What you did meanwhile is also important to understand what's happening so, please, give more details.

---

### Post by mandarpowale on 2015-04-13
A reboot fixed that problem. (I have re-installed the OS, hence i needed to do this again)

---

