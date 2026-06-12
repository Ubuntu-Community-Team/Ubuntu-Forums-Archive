---
title: "New Error with Java, worked fine yesterday"
date: 2007-12-30
forum: General Help
---

### Post by bryanosaurus on 2007-12-30
I've been using this java app, JNetCube.jar - which is essentially just a basic start/stop timer for solving the rubiks cube. It has been working fine, and then today it just wouldn't work. When I try to run it from the terminal i get this error:

bryanosaurus@bryanosaurus:~/Desktop$ java -jar JNetCube.jar
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:42: error: lexical error or unexpected token, expected valid token

And then the window pops up for the timer, but with a plain grey screen that just hangs there. 

Any help would be appreciated

---

### Post by erfahren on 2007-12-30
looks like a problem with the theme. you could try switching back to the default Human theme and try it.

or try putting the JNetCube.jar in your home directory (not on Desktop) and press Alt+F2 and run the command from it, (If that works you could easily create a little script to run it and put the JNetCube.jar pretty much anywhere. - I can tell you how to do that if you want.)

---

### Post by jespdj on 2007-12-30
Which version of Java are you using?

Ubuntu, like most Linux distributions today, comes with GNU Java by default. Unfortunately GNU Java isn't a very good version of Java; it is slow and incomplete. Install Sun's Java 6 instead:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
And make sure that Sun Java 6 is the default Java used on your system by entering this command and selecting Sun Java 1.6.0 from the menu that appears:
```
sudo update-alternatives --config java
```

The error message you get doesn't look like it's something that has to do with Java. Maybe you have GTK theme files that are somehow messed up. Try switching to another desktop theme.

---

### Post by bryanosaurus on 2007-12-30
I have Sun's Java, so I'm going to try to play around with the themes. 

thanks!

---

### Post by mexpolk on 2008-02-05
Simply select None in Visual Effects in the Appareance Preferences during installation (System -> Preferences -> Appareance). The same error will appear in the console, but the installer will show the installation wizard.

Best.

---

### Post by fvaresi on 2008-02-09
> **jespdj said:**
> Which version of Java are you using?

Ubuntu, like most Linux distributions today, comes with GNU Java by default. Unfortunately GNU Java isn't a very good version of Java; it is slow and incomplete. Install Sun's Java 6 instead:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
And make sure that Sun Java 6 is the default Java used on your system by entering this command and selecting Sun Java 1.6.0 from the menu that appears:
```
sudo update-alternatives --config java
```

The error message you get doesn't look like it's something that has to do with Java. Maybe you have GTK theme files that are somehow messed up. Try switching to another desktop theme.

I had a similar problem with Charles (it's an HTTP debugging tool) and thought it was a problem with the desktop theme. I was getting the same error as the first post in this thread.

However I tried to switch the default Java as you said and it worked with java-6-sun (i was using java-1.5.0-sun).

Hope this helps. Regards.

Nando

---

