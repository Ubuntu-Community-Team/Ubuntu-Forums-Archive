---
title: "Personal summary of installing JAVA/JRE in Ubuntu 7.04"
date: 2007-05-21
forum: General Help
---

### Post by chunchengch on 2007-05-21
**1.Download Latest JRE (Java Runtime Environment):**
      [http://www.java.com/zh_TW/download/linux_manual.jsp?locale=zh_TW&host=www.java.com:80](http://www.java.com/zh_TW/download/linux_manual.jsp?locale=zh_TW&host=www.java.com:80)

**2.Change the mode of jre-6u1-linux-i586.bin to be executable:**

$ chmod a+x jre-6u1-linux-i586.bin

**3.Create directory /usr/java and move jre-6u1-linux-i586.bin to this directory:**

$ sudo mkdir /usr/java
$ sudo mv jre-6u1-linux-i586.bin /usr/java

**4.Install JRE:**

$ cd /usr/java
$ sudo ./jre-6u1-linux-i586.bin
$ ls
jre1.6.0_01  jre-6u1-linux-i586.bin

**5.Link Mozilla to Java plugin:**

$ whereis mozilla
mozilla: /usr/bin/mozilla /usr/lib/mozilla /usr/X11R6/bin/mozilla /usr/bin/X11/mozilla /usr/share/man/man1/mozilla.1.gz
$ cd /usr/lib/mozilla
$ ln -s /usr/java/jre1.6.0_01/plugin/i386/ns7/libjavaplugin_oji.so

**6.Restart Mozilla and activate Java:**

Edit > Preferences > Contents 

**7.Test JRE (Java Runtime Environment):**

Visit website to test if JRE is installed successfully.

[http://www.java.com/zh_TW/download/help/testvm.xml](http://www.java.com/zh_TW/download/help/testvm.xml)

---

### Post by ghell on 2007-05-21
or just get the sun-java6-jdk sun-java6-jre sun-java6-plugin (note that the plugin only works on 32bit, if you use 64bit Firefox or whatever you wont be able to use the sun plugin AFAIK) etc from the repositories and then use update-alternatives --config java to select the sun java. You may also have to set sun java to default in eclipse if you use it.

---

