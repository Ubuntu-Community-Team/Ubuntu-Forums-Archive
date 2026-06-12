---
title: "Install Sun-Java5 instead Sun-Java6 available"
date: 2007-04-10
forum: General Help
---

### Post by terciof on 2007-04-10
Hi All!

I'm just installed a 6.10 server and for my surprise, there's only Sun-Java6-JDK avaiable.

I'm using a software that is not compatible with version 6 only 5.

I have the Java 5 .DEB files, but has a lot of dependences....

Is there a way to install Java 5 instead Java 6 directly with apt-get install?

Thanks!

0x3333

---

### Post by Malakia on 2007-04-11
Type this in the command line

```
sudo aptitude install sun-java5-jdk
```

I tried it in feisty and it worked and here is the link to where I found out how to do it. 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0")

You can use apt-get instead of aptitude if you want. Also there are some steps to follow after installing JDK.

---

### Post by terciof on 2007-04-11
That's the problem!

There's no sun-java5 available...

But it's OK, I installed every package by hand! Using dpkg -i....

Thanks!!

---

### Post by phossal on 2007-04-14
You can also install Java 5 using the tutorial in my Sig. It's generally easier. It doesn't use packages, which are just additional wrappers around SUN's .bin files. That means you can update (or downgrade) as necessary, and install as many JDK's as you want. SUN makes all of their previous versions available.

---

