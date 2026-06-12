---
title: "Class path for java"
date: 2008-05-22
forum: General Help
---

### Post by versatile36 on 2008-05-22
I have installed jdk-6u4-linux-i586.bin which is downloaded from sun.java.com.
i have installed the .bin file in /usr/java/jdk1.6.0_04 ..How do i set class path for it ? i have searched in google but none of my trials are success can any one plz help me?

---

### Post by AaronMT on 2008-05-22
I am not sure what you downloaded but the Sun Java 6 SDK is in the repositories.

```
sudo apt-get install sun-java6-jdk
```

This installs the JDK as well as sets up the class path.

If you already know what you want to set JAVA_HOME and CLASSPATH to, you can just run

```
sudo gedit /etc/environment
``` and then add a line for each variable

---

### Post by versatile36 on 2008-05-22
@ AaronMt thxs for ur reponse ..

i have installed successfully the bin file and i want to set the class path..what must be the content of /etc/environment to set the class path for java?

---

### Post by ludovicc on 2008-05-25
What do you want to do here? The global classpath that you set up in /etc/environment is hardly useful. Most Java programs have a start script which sets up the classpath for their needs.

---

