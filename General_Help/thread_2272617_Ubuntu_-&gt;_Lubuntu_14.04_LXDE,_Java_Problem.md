---
title: "Ubuntu -&gt; Lubuntu 14.04 LXDE, Java Problem"
date: 2015-04-08
forum: General Help
---

### Post by kaneda2 on 2015-04-08
Hello Community,

i successfully installed today lubuntu 14.04 LXDE.
Now i stuck with Java.

How i installed java:
   sudo add-apt-repository ppa:webupd8team/java
   sudo apt-get update
   sudo apt-get install oracle-java8-installer
   sudo apt-get install oracle-java8-set-default

It worked, "java -version" shows the correct version.
 If i rightclick the .jar application it also shows "Open with Java 8 Runetime"

But it won't open up? Right now, i have no idea. Double click, or open with etc, just nothing happens..

Maybe someone have an idea?

---

### Post by QIII on 2015-04-08
Hello!

What happens if you issue the following command in the terminal:

```
java -jar </path/to/yourfile.jar>
```

By the way, a .jar is not, strictly speaking, an application -- until it is consumed by the JVM.  A .jar only runs in the context of the JVM.

---

### Post by kaneda2 on 2015-04-08
It doesn't work.
After rebooting the VPS i saw that Java 8 Runetime won't show up in the context menu, by right clicking the file.
All other Java related things are showing up java console/java mission control/java webstart etc...
I have no idea what to do atm.

[IMG]http://i.imgur.com/sOpOfsT.jpg[/IMG]

Its showing under Applications. Also via java -version, still all correct.
I try'd to run a Java Game inside the Browser, that works aswell.

But the .jar file doesnt wanna open up :/

---

### Post by kaneda2 on 2015-04-08
Oh... After some more testing, i got closer... 
Seems something else is missing, because java put me out this info:

 Error - GLX extension is not supported
    GLX version 1.3 or higher is required
Xlib:  extension "RANDR" missing on display ":1".

Hmmm...

EDIT:
For test purpose i downloaded Minecraft.jar
No Problems, it opens, and puts out the same error message in Java.

So, thats probably not the case.
I had a Gnome Core before, and there it was working fine.

Somehow i think the minimal desktop of lubuntu is missing a simple thing to make it work, like everywhere else.

---

### Post by kaneda2 on 2015-04-08
Anyone know what Gnome Core does have, and Lubuntu (minimal desktop) in that java case doesn't ?

---

### Post by Vladlenin5000 on 2015-04-08
> **kaneda2 said:**
> Anyone know what Gnome Core does have, and Lubuntu (minimal desktop) in that java case doesn't ?

No relevant differences and nothing regarding Java support, which is something you install. As such, you should check what Java version have you installed in the previous Ubuntu.

---

### Post by kaneda2 on 2015-04-08
It's the same Java Version on both.
If i Install GnomeCore ontop of that installation, it runs suprisingly.

---

### Post by kaneda2 on 2015-04-08
After many hours later, i try'd this
sudo apt-get install gtk+-3.0

Seems to be working fine. I gonna make a new clear installation now, because i tested to many things. :lolflag:

---

