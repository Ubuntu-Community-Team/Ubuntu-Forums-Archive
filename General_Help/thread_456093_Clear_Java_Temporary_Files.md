---
title: "Clear Java Temporary Files"
date: 2007-05-27
forum: General Help
---

### Post by drs305 on 2007-05-27
How do you clear Java temp files in Ubuntu (and where are they)? In order to access a company web site, a windows user suggested clearing the temporary Java files by going through the Control Panel, Java, Settings ...  Since I don't use windows and can't find the temp files he's referring to, can someone recommend a similar action in linux?  The problem stems from Java hanging up and not loading on the site's initial request to load the Java applet.

Thanks.

---

### Post by MoLE on 2007-06-03
If you've installed the latest version of Sun's Java 6 on ubuntu feisty, then you should find a shortcut on the System --> Preferences menu to the Java Plugin control panel.  This allows you access to the java file cache, and to clear it if you wish.

On my system, the cache is under ~/.java/deployment/cache directory.

I can't speak for other installations of Java on other Linuxes though.

---

