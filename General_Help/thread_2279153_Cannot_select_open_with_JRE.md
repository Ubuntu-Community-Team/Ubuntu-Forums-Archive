---
title: "Cannot select open with JRE"
date: 2015-05-21
forum: General Help
---

### Post by d3ngar on 2015-05-21
Hi,

until recently I was able to select the JRE as an option to open JAR files with. That option has disappeared, although I didn't uninstall the JRE.
I find it quite annoying that I have to start Java apps via the command line now, instead of double clicking. How can I get this back?

Thanks,

Chris

---

### Post by monkeybrain20122 on 2015-05-21
Basically the openjdk-java.desktop file is not installed somehow. You can create one yourself.

In the terminal type 
```
 gksudo gedit /usr/share/applications/openjdk-8-java.desktop

```

Cut and paste these into  the text editor and save
```
[Desktop Entry]
Name=OpenJDK Java 8 Runtime
Name[fi]=OpenJDK Java 8 - ajonaikainen ympäristö
Comment=OpenJDK Java 8 Runtime
Comment[fi]=OpenJDK Java 8 - ajonaikainen ympäristö
Keywords=java;runtime
Exec=cautious-launcher %f /usr/bin/java -jar
Terminal=false
Type=Application
Icon=openjdk-8
MimeType=application/x-java-archive;application/java-archive;application/x-jar;
NoDisplay=true
```


**You should change '8' to '7' if you have openjdk7 instead of 8 installed in your system.**

Now right click the jar file and go to Properties > Open with you should see the icon for OpenJDk runtime showing up and you can  set it to default.

Edited: I copied and pasted the .desktop file from Trusty, it can be simpler.

---

### Post by corti-nico on 2015-05-21
> **monkeybrain20122 said:**
> Basically the openjdk-java.desktop file is not installed somehow. You can create one yourself.

In the terminal type 
```
 gksudo gedit /usr/share/applications/openjdk-8-java.desktop

```

Cut and paste these into  the text editor and save
```
[Desktop Entry]
Name=OpenJDK Java 8 Runtime
Name[fi]=OpenJDK Java 8 - ajonaikainen ympäristö
Comment=OpenJDK Java 8 Runtime
Comment[fi]=OpenJDK Java 8 - ajonaikainen ympäristö
Keywords=java;runtime
Exec=cautious-launcher %f /usr/bin/java -jar
Terminal=false
Type=Application
Icon=openjdk-8
MimeType=application/x-java-archive;application/java-archive;application/x-jar;
NoDisplay=true
```


You should change '8' to '7' if you gave openjdk8 instead of 7 installed in your system.

Now right click the jar file and go to Properties you should see the icon for java showing up and you can  set it to default.

To be sure you can even force unity to reload .desktop files. You can find commands in this answer [http://askubuntu.com/a/447703/410450](http://askubuntu.com/a/447703/410450)

---

### Post by monkeybrain20122 on 2015-05-21
> **corti-nico said:**
> To be sure you can even force unity to reload .desktop files. You can find commands in this answer [http://askubuntu.com/a/447703/410450](http://askubuntu.com/a/447703/410450)

Has nothing to with reloading unity, the .desktop file is not installed in 15.04 for some reasons, so it doesn't show up in  Nautilus' context menu.

---

### Post by corti-nico on 2015-05-21
> **monkeybrain20122 said:**
> Has nothing to with reloading unity, the .desktop file is not installed in 15.04 for some reasons, so it doesn't show up in  Nautilus' context menu.

My reply was a suggestion to do after your instructions ;)

---

### Post by d3ngar on 2015-05-29
I'm sorry, I forgot to reply on the thread. This really works for me!

Chris

---

