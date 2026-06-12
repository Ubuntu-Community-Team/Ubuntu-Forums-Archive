---
title: "How can I run Jgrasp on ubuntu ?"
date: 2013-10-10
forum: General Help
---

### Post by raghadm on 2013-10-10
Hi every body

I'm a beginner  Ubuntu user 
I tried to download jgrasp on my laptop from here 
[http://spider.eng.auburn.edu/user-cgi/grasp/grasp.pl?;dl=download_jgrasp.html](http://spider.eng.auburn.edu/user-cgi/grasp/grasp.pl?;dl=download_jgrasp.html)
But I don't how what should I do to run it ?

Please help 
Thanks

---

### Post by slickymaster on 2013-10-10
Hi [COLOR=#000000]raghadm, welcome to the forums.[/COLOR]

I've never used jGRASP, but as it is a Java application first of all you have to ensure that you have Java installed properly. Open a terminal and run the following:```
java -version
```it should output something like:```
~$ java -version
java version "1.7.0_40"
Java(TM) SE Runtime Environment (build 1.7.0_40-b43)
Java HotSpot(TM) Client VM (build 24.0-b56, mixed mode)
```If you don't have Java, all you have to do is to install it. At terminal, run:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```Afterwards, all you have to do is to navigate to the folder where your downloaded Jgrasp is and unzip it:```
cd /path/to/folder/contaigning/jgrasp.zip
unzip jgrasp200_03.zip
jgrasp/bin/jgrasp
```
Don't forget that your Java "bin" directory must be on your system PATH for it to run.

---

