---
title: "Cannot invoke Java, even though it is installed"
date: 2012-11-02
forum: General Help
---

### Post by Wgimson on 2012-11-02
So I'm using some parsing tools (JFlex and JCup) for a project, and as a result I *don't* want to use the **OpenJDK** ,or Iced Tea that were on my system, but rather **Sun's version 7 jdk,** which I already have downloaded.

 So I set the** JAVA_HOME** and** PATH** variables to the directory I downloaded** jdk7** to and it's bin sub-directory, but the system was still invoking **Openjdk**, so I removed it ***and* **removed the symbolic link** java **in **etc/alternatives**, becuase I thought that's what was causing the behavior. 

This latter part I believe has now caused a problem, since now I cannot invoke** java **at all, even when I am in the** jdk1.7.04_04** directory of the version I installed and want to use! I get ....

```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
```Here are the environment settings in my .bashrc file...

```

JAVA_HOME=/user/local/jdk1.7.0_04
 export JAVA_HOME  

 PATH=$PATH:$JAVA_HOME/bin:
 export PATH

 PATH=$PATH:$JAVA_HOME/jre/lib/ext:
 export PATH

 CLASSPATH=$JAVA_HOME/lib:.
 export CLASSPATH
```So what do you guys think? Is the problem that I have to recreate the symbolic link in /etc/alternatives and link it to /usr/local/jdk1.7.04_04/bin?


EDIT - Sorry, I made a mistake. Java most certainly *does* work when I am in the same directory as it's /bin, just nowhere else. I knew that didn't make sense. So, the question is why aren't my environment variable settings allowing me to use java anywhere in the file system like I should be able to?

---

