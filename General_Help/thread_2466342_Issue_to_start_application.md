---
title: "Issue to start application"
date: 2021-08-26
forum: General Help
---

### Post by peter-1984 on 2021-08-26
[COLOR=#000000][FONT=&quot]Hi,[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]How to start "org.eclipse.equinox.launcher_1.6.200.v20210416-2027.jar" within Ubuntu 20.04?[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]-startup[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]plugins/org.eclipse.equinox.launcher_1.6.200.v20210416-2027.jar[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]--launcher.library[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.2.200.v20210429-1609[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]-product[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]org.eclipse.epp.package.java.product[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]-showsplash[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]org.eclipse.epp.package.common[/FONT][/COLOR]

---

### Post by vanadium on 2021-08-26
A *.jar* file is run with the command "java <file>".

---

### Post by slickymaster on 2021-08-26
*Thread moved to **General Help**.*

---

### Post by peter-1984 on 2021-08-26
Can you help to issue below?


root@may-VirtualBox:/home/may/Desktop/Eclipse Java/plugins# java org.eclipse.equinox.launcher_1.6.200.v20210416-2027
Error: Could not find or load main class org.eclipse.equinox.launcher_1.6.200.v20210416-2027
Caused by: java.lang.ClassNotFoundException: org.eclipse.equinox.launcher_1.6.200.v20210416-2027

---

