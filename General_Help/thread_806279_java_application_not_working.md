---
title: "java application not working"
date: 2008-05-24
forum: General Help
---

### Post by cylux on 2008-05-24
Hey guys, I have a java application I wrote, but when I run

```
java appname
```

It does nothing, the prompt just goes to the next line. On Windows the same application with the same commands works perfectly.

Any help is appreciated

---

### Post by omi291 on 2008-05-24
have you compiled the java source code with

```
javac appname.java?
```

If that still doesn't work, then it could be that you don't have the SDK installed, and to install it just type:

```
sudo apt-get install sun-java6-jdk
```

into the terminal

---

### Post by ludovicc on 2008-05-25
Also, check your classpath. 

Try this command:

java -cp . appname

---

