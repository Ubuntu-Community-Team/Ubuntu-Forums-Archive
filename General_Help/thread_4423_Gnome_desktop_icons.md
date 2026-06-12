---
title: "Gnome desktop icons"
date: 2004-11-15
forum: General Help
---

### Post by Klunk on 2004-11-15
I use my Linux box for application development and I use eclipse as my IDE of choice. I am actually attempting to write an application without paying for any software :D, hence Linux, Java, eclipse free plugins for eclipse etc.

Anyway, back to my question, I need certain environment variables to run eclipse, which are all in my .profile, however if I put a shortcut on my gnome desktop it does not get the correct environment. How do I make sure my desktop has the same environment as my shell ?

---

### Post by HungSquirrel on 2004-11-15
[QUOTE=Klunk]I use my Linux box for application development and I use eclipse as my IDE of choice. I am actually attempting to write an application without paying for any software :D, hence Linux, Java, eclipse free plugins for eclipse etc.

Anyway, back to my question, I need certain environment variables to run eclipse, which are all in my .profile, however if I put a shortcut on my gnome desktop it does not get the correct environment. How do I make sure my desktop has the same environment as my shell ?[/QUOTE]
 I had that problem no matter how many environment variables I set for Eclipse.  My scientific conclusion is that Eclipse is retarded.

I assume the problem you are having is Eclipse cannot find your JRE.  I made a symbolic link in the Eclipse directory to the JRE.  For example, on a system with Eclipse at /usr/local/eclipse and a JDK at /usr/local/java with a JRE at /usr/local/java/jre, you may get around the problem by doing this:

```
sudo ln -s /usr/local/java/jre /usr/local/eclipse/jre
```

---

