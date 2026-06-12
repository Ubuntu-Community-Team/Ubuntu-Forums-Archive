---
title: "jbidwatcher"
date: 2016-02-10
forum: General Help
---

### Post by linuxhippy on 2016-02-10
Has anybody gotten jbidwatcher to work in ubuntu 15.10?  I had it working in previous ubuntu installs but am having trouble now.  I have iced tea java installed and it needs sun java.  I went to [http://java.com](http://java.com) and downloaded the linux64 tar.gz file and extracted it in /usr/java but that's where I'm stuck.  The installation instructions at that site end at extracting the files.  

How do I install the new java?

I tried specifying my java version with sudo update-alternatives --config java but only got this:

There is only one alternative in link group java (providing /usr/bin/java): /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
Nothing to configure.

---

### Post by steve_mc on 2016-02-10
Jbidwatcher works with openjdk8 qnd ubuntu 15.10. That is what i have installed,and jbidwatcher works on my computer. So installing openjdk from the software center may be an easier option. Also edit the jbidwacher.sh file. Change java -cp to java -Xdebug -cp. I don't know why the -Xdebug flag works, but the program would not run without it.

---

### Post by linuxhippy on 2016-02-10
That worked-thanks!

---

