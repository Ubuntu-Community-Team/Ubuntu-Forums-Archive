---
title: "Java Iriverter crash"
date: 2008-05-20
forum: General Help
---

### Post by Sonja on 2008-05-20
I get this error:

```
sonja@sonja:~$ iriverter
!!! An unhandled exception occured: class java.lang.StringIndexOutOfBoundsException
--- iriverter 0.16
--- 
--- Settings:
--- videoBitrate=
--- audioBitrate=
--- currentProfile=d2
--- frameRate=
--- dimensions=
--- autoSplit=
--- splitTime=
--- autoSync=true
--- audioDelay=0
--- 
!!! String index out of range: -1
!!! 
!!! java.lang.String.substring(String.java:1949)
!!! org.thestaticvoid.iriverter.Dimensions.<init>(Dimensions.java:12)
!!! org.thestaticvoid.iriverter.Profile.getDimensions(Profile.java:72)
!!! org.thestaticvoid.iriverter.ConverterUI.profileChanged(ConverterUI.java:502)
!!! org.thestaticvoid.iriverter.ConverterUI.setupMenus(ConverterUI.java:275)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:41)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 

```

---

### Post by Sonja on 2008-05-20
How do I delete this post? I posted it in [http://ubuntuforums.org/showthread.php?p=5004830](http://ubuntuforums.org/showthread.php?p=5004830) instead.

---

### Post by MaindotC on 2008-05-20
I'll report it for you.

---

