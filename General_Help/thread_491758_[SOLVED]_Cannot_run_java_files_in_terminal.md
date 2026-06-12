---
title: "[SOLVED] Cannot run java files in terminal"
date: 2007-07-04
forum: General Help
---

### Post by trenog on 2007-07-04
Hey there. 

So, for some reason I managed to get the javac part of java to work, however I cannot get the java part to work. Got any ideas as to why?

This is just some additional information to stew over in case it helps:

```
trenog@trenog-desktop:~$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)
```
```

trenog@trenog-desktop:~$ javac -version
javac 1.5.0_11
```

```
trenog@trenog-desktop:~$ echo $PATH
/usr/lib/j2sdk1.5-sun/bin:/home/trenog/javokapi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

```
trenog@trenog-desktop:~$ echo $CLASSPATH
/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar:/home/trenog/javokapi/bin/xmlrpc.jar
```

Thanks

---

### Post by FuturePilot on 2007-07-04
What exactly are you trying to run? Is it a .jar file? If it is try ```
java -jar /path/to/file.jar
```

---

### Post by trenog on 2007-07-04
I'm just trying to run any class file.

I'm able to compile, just not to run. I get that all too common no class def error:

```
trenog@trenog-desktop:~/java$ javac test.java
trenog@trenog-desktop:~/java$ java test
Exception in thread "main" java.lang.NoClassDefFoundError: test
```

And this is on the most basic kind of java file, one with only a single println saying "test".

---

### Post by slackorama on 2007-07-04
It looks like you are explicitly setting the classpath without the current directory.

Try adding "." to your classpath and then running "java test".  Alternately you could run
```
java -cp "." test
```

---

### Post by trenog on 2007-07-04
Well that seems to have worked (the "."). 

However, is there a long term solution that exists such that I can run a .class file in select or all directories without adding a "." each time?

---

### Post by slackorama on 2007-07-04
Just add it to wherever your classpath is set.
```

export CLASSPATH=.:/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar:/home/trenog/javokapi/bin/xmlrpc.jar
```

---

### Post by trenog on 2007-07-05
Awesome, it worked. Solved some other problems I was having as well.

Thanks

---

### Post by checho4 on 2007-07-15
I'm a beginner with Java and am learning to program.  I seem to be having trouble opening my class files.  I have javac 1.5.0_11, but when i type "java -version", I get this:

```
checho4@checho:~/Desktop$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

```

I'm running Kubuntu 7.04 64-bit.  Any help is greatly appreciated!

---

