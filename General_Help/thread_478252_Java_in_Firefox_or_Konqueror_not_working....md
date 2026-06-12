---
title: "Java in Firefox or Konqueror not working..."
date: 2007-06-19
forum: General Help
---

### Post by darkmaster on 2007-06-19
So, I installed Java 6 using the following guides:

[http://ubuntuforums.org/showthread.php?t=477808&highlight=java](http://ubuntuforums.org/showthread.php?t=477808&highlight=java)
[http://ubuntuforums.org/showthread.php?t=449899&highlight=java](http://ubuntuforums.org/showthread.php?t=449899&highlight=java)
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

And I also used Automatix. Nothing served as a good result. If I open FIrefox and enter
```
about:plugins
```
I get the following info about java:
```
Java(TM) Plug-in 1.6.0-b105

    Nome file: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

Tipo MIME 	Descrizione 	Estensione 	Attivo
application/x-java-vm 	Java 		Sì
application/x-java-applet 	Java 		Sì
application/x-java-applet;version=1.1 	Java 		Sì
application/x-java-applet;version=1.1.1 	Java 		Sì
application/x-java-applet;version=1.1.2 	Java 		Sì
application/x-java-applet;version=1.1.3 	Java 		Sì
application/x-java-applet;version=1.2 	Java 		Sì
application/x-java-applet;version=1.2.1 	Java 		Sì
application/x-java-applet;version=1.2.2 	Java 		Sì
application/x-java-applet;version=1.3 	Java 		Sì
application/x-java-applet;version=1.3.1 	Java 		Sì
application/x-java-applet;version=1.4 	Java 		Sì
application/x-java-applet;version=1.4.1 	Java 		Sì
application/x-java-applet;version=1.4.2 	Java 		Sì
application/x-java-applet;version=1.5 	Java 		Sì
application/x-java-applet;version=1.6 	Java 		Sì
application/x-java-applet;jpi-version=1.6 	Java 		Sì
application/x-java-bean 	Java 		Sì
application/x-java-bean;version=1.1 	Java 		Sì
application/x-java-bean;version=1.1.1 	Java 		Sì
application/x-java-bean;version=1.1.2 	Java 		Sì
application/x-java-bean;version=1.1.3 	Java 		Sì
application/x-java-bean;version=1.2 	Java 		Sì
application/x-java-bean;version=1.2.1 	Java 		Sì
application/x-java-bean;version=1.2.2 	Java 		Sì
application/x-java-bean;version=1.3 	Java 		Sì
application/x-java-bean;version=1.3.1 	Java 		Sì
application/x-java-bean;version=1.4 	Java 		Sì
application/x-java-bean;version=1.4.1 	Java 		Sì
application/x-java-bean;version=1.4.2 	Java 		Sì
application/x-java-bean;version=1.5 	Java 		Sì
application/x-java-bean;version=1.6 	Java 		Sì
application/x-java-bean;jpi-version=1.6 	Java
```

So it looks like it is correctly installed but.... it doesn't work.
If I try to enter this site, for example:

[http://www-ui.is.s.u-tokyo.ac.jp/~takeo/teddy/teddy/teddy.html](http://www-ui.is.s.u-tokyo.ac.jp/~takeo/teddy/teddy/teddy.html)

A gray window opens up with the symbol of java on the decorator but in the middle of this window there's only written: Java applet window. Nice, huh? If I download the same app and run it with 
```
java -jar filename.jar
```
It works fine, so I guess it's a plugin problem.
Plus, if I try to load the page with Konqueror, the popup window with java applet doesn't even appear! Weird...

I had the same problem with another page too but nobody could help me with that problem too. Here's the llink:

[http://ubuntuforums.org/showthread.php?t=458921](http://ubuntuforums.org/showthread.php?t=458921)

I'm starting to get annoyed with this :( How is it possible that a banal java plugin that should work great out of the box with any OS doesn't with Ubuntu??? In Windows it works dammit and Java is an opensource project now!! Please, please, someone help me.

---

### Post by tbresson on 2007-06-19
Try and go to your mozilla plugin dir and make a link to the java you have installed.

This example is taken from java.com:
ln -s /usr/java/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so

---

