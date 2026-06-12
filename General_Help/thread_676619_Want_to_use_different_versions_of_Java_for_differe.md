---
title: "Want to use different versions of Java for different apps"
date: 2008-01-23
forum: General Help
---

### Post by arcanum on 2008-01-23
Basically Azureus runs best with the Sun Java 6 runtime environment, on my machine it's located at  /usr/lib/jvm/java-6-sun/jre/bin/java.
However, I also run iriverter which just won't have it. It needs gcj to run, at /usr/lib/jvm/java-gcj/jre/bin/java.

At the moment I have sun java as my default, however I want to call on gcj to run iriverter. If anyone has a (simple) solution I would be very grateful.
I was hoping just to change the launcher command but I haven't found any success so far.

-arcanum

---

### Post by arcanum on 2008-01-24
No ideas?
I read in [[COLOR="DarkRed"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=452869") that I need to make a script, but I couldn't seem to get it working. Any help would be appreciated as I'm still quite new to Linux.

-arcanum

---

### Post by cozmicharlie on 2008-01-24
There is a neat trick in Ubuntu for switching java versions:
sudo update-alternatives --config java

---

### Post by SyL on 2008-01-24
Here is a very interesting article answering (with clear and useful example) exactly your question:
[http://blog.stevenkroon.com/2006/08/29/debian-update-alternatives/]("http://blog.stevenkroon.com/2006/08/29/debian-update-alternatives/")

---

