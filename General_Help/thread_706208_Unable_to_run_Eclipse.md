---
title: "Unable to run Eclipse"
date: 2008-02-24
forum: General Help
---

### Post by debtaru on 2008-02-24
I get the following message when I launch eclipse:



JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /opt/eclipse/eclipse
-name Eclipse
--launcher.library /opt/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.2.R331_v20071019/eclipse_1021.so
-startup /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-exitdata 200014
-clean
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar 



I have installed eclipse-jee-europa-fall2-linux

I have eclipse installed at /opt/eclipse directory

Please help me resolve.

---

### Post by ditsch on 2008-02-24
Which Java VM are you using?

---

### Post by belda on 2008-02-24
I got the same some time ago, check if you have jre and jdk installed properly...

---

### Post by kaens on 2008-02-24
If your jde and jdk is properly installed, and you continue to have problems getting eclipse to run, you may want to consider [easyeclipse/]("http://www.easyeclipse.org/site/home/")

---

