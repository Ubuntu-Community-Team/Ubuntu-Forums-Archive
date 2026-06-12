---
title: "Java does not recognize new package"
date: 2008-02-17
forum: General Help
---

### Post by Johnny K on 2008-02-17
I need to write a Java program that uses the [iText]("http://www.lowagie.com/iText/") API. So I went into Synaptic and installed the package libitext-java, which creates /usr/share/java/itext.jar and /usr/share/java/itext-1.4.5.jar

But for some reason, the Java compiler still cannot import iText classes, and gives the error below:
```
Test.java:4: package com.lowagie does not exist
import com.lowagie.text;

```

I am currently using the /usr/lib/jvm/java-1.5.0-sun compiler, rather than the one Ubuntu uses by default. Could that have something to do with it?

Thanks in advance :)

---

### Post by jken146 on 2008-02-17
When you import the package into your class, use the absolute path to it.  That should work.

---

### Post by Johnny K on 2008-02-17
***edit:***
I got everything to work. Thanks for the help, jken146.
For anyone else that might stumble upon this thread, here is my solution. If you have had a similar problem and need to get the Java compiler to recognize a new library, do the following:

[LIST=1]
[*]Install the library via Synaptic
[*]Still in Synaptic, right-click on the library package, clicked "Installed Files", and find, in the list, the location of a .jar file (in my case, /usr/share/java/itext.jar and /usr/share/java/itext-1.4.5)
[*]In terminal do the following:
```
sudo gedit /etc/jvm
```
[*]Locate the first line that is not empty or preceded by a # (in my case, /usr/lib/jvm/java-1.5.0-sun)
[*]In terminal do the following, replacing the directories with the ones you found in steps 2 and 4. Also, append /jre/lib/ext to the second directory as I did below:
[*]```
gksudo nautilus /usr/share/java
gksudo nautilus /usr/lib/jvm/java-1.5.0-sun/jre/lib/ext
```
[*]Copy the library's .jar files (in my case, itext.jar and itext-1.4.5.jar) from the first directory to the second
[/LIST]

And that's it. The Java compiler should now recognize your new library. If you have any questions, please feel free to send me a private message.

---

