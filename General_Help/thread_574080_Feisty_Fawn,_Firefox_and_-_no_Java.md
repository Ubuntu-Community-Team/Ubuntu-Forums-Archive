---
title: "Feisty Fawn, Firefox and - no Java"
date: 2007-10-12
forum: General Help
---

### Post by chilisastry on 2007-10-12
I am using Feisty Fawn, Firefox v2.0.0.6,  Since Java pages don't work, I installed the plug-in JRE1.6.0_03 according to the instructions at Sun's web-site.  All steps worked fine, except the final test page.  Obviously the link to the Java Plug-in is not properly set up.  Of course, Java is selected in Firefox Preferences.

I set up links in the following directories:

/usr/lib/mozilla/plugins

/usr/lib/firefox/plugins

For example, here's the directory listing for the firefox folder:

chili@chili-desktop:/usr/lib/firefox/plugins$ ls -l
total 248
-rwxr-xr-x 3 root root 236012 2007-09-24 23:10 libjavaplugin_oji.so
lrwxrwxrwx 1 root root     36 2007-08-30 00:09 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root     37 2007-08-30 00:09 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root     34 2007-08-30 00:09 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root     35 2007-08-30 00:09 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root     36 2007-08-30 00:09 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root     37 2007-08-30 00:09 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root     42 2007-08-30 00:09 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root     43 2007-08-30 00:09 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root   8936 2007-07-31 06:53 libunixprintplugin.so
chili@chili-desktop:/usr/lib/firefox/plugins$ 


Any words of wisdom?  I'm surprised Feisty Fawn does not come with the Java plugin all set up.  With OpenOffice, I am sure there is a JRE installed already.

---

### Post by TheWizzard on 2007-10-12
sudo aptitude install sun-java5-jre sun-java5-plugin 
accept defaults
sudo update-alternatives --config java
choose: J2SE

---

### Post by chilisastry on 2007-10-12
Tried it but did not work.  Not even after a restart.

For the second command, sudo update.., the choices were 1. and 2.  I chose 2, the default.

---

### Post by chilisastry on 2007-10-12
Do i have to log on as root, or do I have to change directory to some other location before thee commands?

---

### Post by TheWizzard on 2007-10-13
> **chilisastry said:**
> Do i have to log on as root, or do I have to change directory to some other location before thee commands?

the sudo command is sufficient

---

### Post by TheWizzard on 2007-10-13
> **chilisastry said:**
> Tried it but did not work.  Not even after a restart.

For the second command, sudo update.., the choices were 1. and 2.  I chose 2, the default.

what are the choices?

---

### Post by chilisastry on 2007-10-13
Here's the transaction trace:

chili@chili-desktop:~$ sudo aptitude install sun-java5-jre sun-java5-plugin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
chili@chili-desktop:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
chili@chili-desktop:~$ 


I did try the same procedure with java6, that's why there are three choices now.

Chili

---

### Post by strabes on 2007-10-13
Installing the ubuntu-restricted-extras package will install the JRE.

---

### Post by TheWizzard on 2007-10-13
looks like jre is installed on his pc.

---

