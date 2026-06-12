---
title: "Logisim not doing anything"
date: 2018-09-11
forum: General Help
---

### Post by whatishappening on 2018-09-11
I downloaded it first by: sudo apt-get update sudo apt-get install logisim  The problem is that when I try to launch the program, nothing happens at all  Afterwards I tried downloading it from the Ubuntu software center, but the same happens.  If anyone known what could cause this problem, i'd greatly appreciate a bit of help

---

### Post by Holger_Gehrke on 2018-09-11
Have you tried starting it from a terminal by entering 'logisim' ? If you do, you'll probably get this error message:
```

Exception in thread "main" java.awt.AWTError: Assistive Technology not found: org.GNOME.Accessibility.AtkWrapper

```with a stack trace

If that's what happens, the solution is simple, provided you don't need support for Accessibility. Open a terminal. Check the version of java by entering 'java -version'. For Open JDK 10 enter```
sudo nano /etc/java-11-openjdk/accessibility.properties
```
For Open JDK 8 enter```
sudo nano /etc/java-8-openjdk/accessibility.properties
```
In that file there is a single line that does not begin with a '#' (meaning this line is not a comment). Put a '#' in front of that line, thereby making java disregard that line. Save, exit, enjoy.

Holger

---

### Post by whatishappening on 2018-09-12
Thank you so much, it worked.

---

