---
title: "enable java 7 in ubuntu 12.10"
date: 2012-11-08
forum: General Help
---

### Post by workaround on 2012-11-08
what is the way to enable java 7 in ubuntu 12.10 mozila firefox? :confused:
Thanks.

---

### Post by pkadeel on 2012-11-08
> **workaround said:**
> what is the way to enable java 7 in ubuntu 12.10 mozila firefox? :confused:
Thanks.
the java browser plugin can be enabled and disabled from firefox menu Tools > Add-ons

I guess what you wanted to ask was how to install java on ubuntu 12.10. If that is the case then you can do that from software centre. Software title is "OpenJDK Java 7 Runtime"

Alternately you can install from command line by entering the following install command
```

sudo apt-get install openjdk-7-jre icedtea-7-plugin

```

---

### Post by Abhinav Kumar on 2012-11-08
> **workaround said:**
> what is the way to enable java 7 in ubuntu 12.10 mozila firefox? :confused:
Thanks.
Hi

I don't know whether it will work for ubuntu 12.10 but the following steps had worked for ubuntu 10.10

Download latest jre package.
Extract it to the home folder
Say the folder is jre-1.7.0.0

You need libnpjp2.so to run java in firefox

So better make a symbolic link of the same name and point it to the the downloaded folder
```

sudo -i
cd /usr/lib/mozilla/plugins
ln -s /home/USERNAME/jre-1.7.0.0/lib/amd64/libnpjp2.so

```
here USERNAME has to be replaced by your username  in whose home folder you had extracted the downloaded package.

Regards,
Abhinav

---

### Post by cottfcfan on 2012-11-08
This should help:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
The 2nd option "Install Oracle Java 7 in Ubuntu via PPA" works flawlessly.

---

### Post by workaround on 2012-11-08
Since Java is already installed I used [pkadeel]("http://ubuntuforums.org/member.php?u=1744160")'s plugin. Interesting it does not say much that it is installed, called "icedtea!?", I guess.
Thanks much.:guitar:

---

