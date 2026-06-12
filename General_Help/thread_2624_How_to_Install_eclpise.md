---
title: "How to Install eclpise?"
date: 2004-10-29
forum: General Help
---

### Post by akamjballar on 2004-10-29
I have the zip file for eclipse. I just don't know what to do after. I have install netbeans, but it gives too many errors. So I just want to try eclipse out.

---

### Post by FLeiXiuS on 2004-10-29
```
unzip filename.zip
```

I'm guessing this will be a source file?

```

cd path/to/directory/created
make
sudo make install

```

That should be how to do it if your compiling from the source.  If not please paste the contents of this ZIP file.

---

### Post by akamjballar on 2004-10-30
This is after I extracted it.

[IMG]http://www.awptical.com/niggaland.jpg[/IMG]

---

### Post by jaboo on 2004-11-01
If you've downloaded Eclipse, then you're good to go. You have to download and install the Java SDK or RE separately. Then just unzip your package into somewhere like /opt. I think execution would be something like /opt/eclipse/eclipse.

---

### Post by HungSquirrel on 2004-11-01
After installing the Java SDK, make sure you add its bin/ directory to your $PATH.  There are numerous threads about $PATH and other environment variables in this forum, so look there for info on how to do this.

---

### Post by Enygma on 2004-11-02
[QUOTE=HungSquirrel]After installing the Java SDK, make sure you add its bin/ directory to your $PATH.  There are numerous threads about $PATH and other environment variables in this forum, so look there for info on how to do this.[/QUOTE]
 When I installed Eclipse it didn't pick up my JDK installation at all. I have to start it like this:
```

eclipse -vm /path/to/jdk/bin -Xmx256M

```

That does the trick.

---

### Post by jaboo on 2004-11-03
Your Java installation is not being picked up by eclipse because you probably do not have the path to java in your environment variables. I would suggest following the Quick Install instructions [here](http://wiki.ubuntulinux.org/Java) under Method 2 to install Java. Not only does it get Java installed as a Debian package, but it also sets up your environment variables so that the path to Java is known.

---

### Post by Enygma on 2004-11-03
[QUOTE=jaboo]Your Java installation is not being picked up by eclipse because you probably do not have the path to java in your environment variables. I would suggest following the Quick Install instructions [here](http://wiki.ubuntulinux.org/Java) under Method 2 to install Java. Not only does it get Java installed as a Debian package, but it also sets up your environment variables so that the path to Java is known.[/QUOTE]
 Just thinking about it I forgot to set the JAVA_HOME env variable, that's probably it. 
Thanks!

---

### Post by jwenting on 2004-11-04
[QUOTE=Enygma]Just thinking about it I forgot to set the JAVA_HOME env variable, that's probably it. 
Thanks![/QUOTE]
 JAVA_HOME is AFAIK indeed needed.

Remember to install Eclipse 3.1M2 or later if you want Tiger support in Eclipse.
Eclipse requires a J2SDK 1.4 or later to run, personally I run it on Tiger (JDK 5.0) which is fine (haven't tried it on my Linux machine as it's too low spec to run Eclipse, good time to brush up those VI skills :) ).

Make sure the environment settings actually take.
I've had trouble getting the appended PATH and JAVA_HOME to appear, depending on your shell you should add them to .profile or .bashrc (or /etc/profile or supposedly /etc/bashrc to make them available to all users).

---

