---
title: "[CLOSED] Package 'oracle-java8-installer' has no installation candidate"
date: 2016-05-23
forum: General Help
---

### Post by benjamin38 on 2016-05-23
Hi All,

Running Lubuntu 16.04
I've added the ppa as per [this]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") link, but when I ```
sudo apt-get install oracle-java8-installer
``` I get this error ```
Package 'oracle-java8-installer' has no installation candidate
```

Note: I had previously removed openjdk* java* icedtea*

What do I need to add or do to install this package?

Interesting thing: LibreOffice's help pop-ups, which require java, are working, even though I seemingly don't have any java installed.

---

### Post by QDR06VV9 on 2016-05-23
Just to check things...what dose this show in the terminal
```
java -version
```
Any way I have seen this before and sometimes it takes a couple of update commands to get it pulled in.
```
sudo apt update
```
Followed by
```
sudo apt install oracle-java8-installer 

```

Or even save some time accepting Oracle's license.
```
echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
```

---

### Post by benjamin38 on 2016-05-23
Thanks for the comment.

As expected, ```
java --version
``` or ```
java -version
``` return
```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.9-jre-headless
 * gcj-5-jre-headless
 * openjdk-8-jre-headless
 * gcj-4.8-jre-headless
 * openjdk-9-jre-headless
Try: sudo apt install <selected package>
```

And ```
sudo apt install oracle-java8-installer
``` returns the same message as before, both before and after ```
sudo apt update
```

---

### Post by QDR06VV9 on 2016-05-23
Well that's not good maybe the Repo is down for some reason.
But here is direct link to Java Installer
[http://www.ubuntuupdates.org/package/webupd8_java/precise/main/base/oracle-java8-installer](http://www.ubuntuupdates.org/package/webupd8_java/precise/main/base/oracle-java8-installer)

And use the method you care to use or install by way of 
```
sudo dpkg -i oracle-java8-installer_8u51+8u51arm-1-webupd8-0_all.deb
```
Regards

---

