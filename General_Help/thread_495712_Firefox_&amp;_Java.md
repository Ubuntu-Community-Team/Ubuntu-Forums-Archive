---
title: "Firefox &amp; Java"
date: 2007-07-08
forum: General Help
---

### Post by Old Pink on 2007-07-08
Suddenly started complaining, fine until today, everything says I need the Java plugin installed, which I've done again, and is installed for certain.

When trying to get on a Java site, Firefox spits this into terminal:
> /usr/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directory/usr/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directoryIt's looking in completely the wrong place there, and I can't create a file there or even a symbolic link. 

```
cannot create regular file `/usr/lib/i386/libjavaplugin_nscp.so': No such file or directory
```Anyone help?

---

### Post by Old Pink on 2007-07-08
Firefox plugins directory has the correct file in there....

---

### Post by Old Pink on 2007-07-08
Reinstalling sun-java5-plugin didn't do it. 

Neither did numerous reboots. 

[img]http://www.filehive.com/files/0708/annoyance.png[/img]

... :(

---

### Post by r0ck80y on 2007-07-08
Try this:
```
rm .mozilla/firefox/pluginreg.dat 
```
Then restart firefox.

---

### Post by cenTrea on 2008-02-23
you should try
# cd /usr/lib
# mkdir i386
# ln -s /usr/java/jrexxx/lib/i386/libjavaplugin_nscp.so /usr/lib/i386
/usr/java/jrexxx/ is the path of Java in your os

---

