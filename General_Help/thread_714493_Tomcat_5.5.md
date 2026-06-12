---
title: "Tomcat 5.5"
date: 2008-03-03
forum: General Help
---

### Post by hebetude on 2008-03-03
Getting this error?  
java.io.FilePermission /path/to logging.properties read

It's related to a bug in tomcat-5.5-20, but still isn't fixed in my .25 version.  You can circumvent this by editing the /etc/init.d/tomcat-5.5 and turning security off.  

Search for TOMCAT5_SECURITY.  This circumvents security measures in tomcat, so only use if you are very trusting.

Welcome to google search you lame *** bug

---

### Post by gustin on 2008-04-25
Another solution is to modify some tomcat security policies as explained in this [article]("http://www.aleph-null.tv/article/20080327-0118-335.xml/Tomcat-5.5-On-Debian:-AccessControlException-for-logging.properties")

---

