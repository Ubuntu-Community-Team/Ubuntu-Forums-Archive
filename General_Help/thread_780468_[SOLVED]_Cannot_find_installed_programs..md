---
title: "[SOLVED] Cannot find installed programs."
date: 2008-05-03
forum: General Help
---

### Post by stevoo on 2008-05-03
I have netbean 5.5.1 and netbeans 6 RC1 installed.

and i wanted to remove them.... 

it seems that i cannot find the installed applications
neither in add/remove OR in package manager.
They are not there
running apt-cache search
 i find this
```
 apt-cache search netbeans
libbeansbinding-java - Beans Binding API
libbeansbinding-java-doc - Beans Binding API
libnb-apisupport1-java - Common NetBeans Platform Development Related Libraries for NetBeans
libnb-ide8-java - Common Integrated Development Environment Libraries for NetBeans
libnb-java1-java - Common Java Related Libraries for NetBeans
libnb-javaparser-java - Parser for the Java language which is good for use in tools
libnb-platform7-devel-java - Build harness for NetBeans Platform
libnb-platform7-java - NetBeans Platform for building rich desktop applications in Java
libnb-platform7-java-doc - NetBeans Platform javadoc
libnb-svnclientadapter-java - High-level Java API to subversion
libswing-layout-java - Extensions to Swing layout
libswing-layout-java-doc - Extensions to Swing layout - contains Javadoc API documentation
netbeans - Integrated Development Environment

```

Now cause i am not sure i didnt do anything. 

Can i get some help into removing those two please

---

### Post by Monicker on 2008-05-03
apt-cache search shows you what is in the repositories and available for install, not whether it is actually installed on your system.

To see what is actually installed:
```

dpkg --get-selections
```

---

### Post by stevoo on 2008-05-03
Well still i cannot find netbeans there 

even when using 

dselect or aptitude


Where did it go  ?

---

### Post by Monicker on 2008-05-03
> **stevoo said:**
> Well still i cannot find netbeans there 

even when using 

dselect or aptitude


Where did it go  ?


How was it installed?  Did you install it from the Ubuntu repositories, or by some other method?

---

### Post by stevoo on 2008-05-04
Netbean 5.5 was installed by the repos, the 6Rc1 was installed by a .deb file.

---

