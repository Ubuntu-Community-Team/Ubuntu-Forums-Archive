---
title: "Oracle Java plugin not working (Firefox or Chrome)"
date: 2014-02-10
forum: General Help
---

### Post by dab5155 on 2014-02-10
I am having issues getting Firefox to recognize my newest java plugin.  I am also having the same issue with Chrome.  I have a 32-bit xubuntu OS.  I uninstalled the previous version of java prior to installing the new version.  I also deleted and re-created the symbolic links for firefox and chrome.  I also checked in the Java configuration tool and noticed the check box was checked to have java enabled.  I also verified java was allowed by default in both browser settings.

When I run java -version, I get the version java version "1.7.0_51" as what is installed.  I double checked and made sure I downloaded the correct tar file(jre-7u51-linux-i586.tar.gz)  I am not using IcedTea.

I also tried uninstalling then reinstalling again, still no luck.  Rebooted several times, cleared all cache from browsers and Java, still nothing.  I need to install java to access my work's VPN access site.  So any help will be appreciated.

---

### Post by ajgreeny on 2014-02-10
Have you installed the icedtea or oracle java plugin package as well as the java jre package

---

### Post by dab5155 on 2014-02-12
My next step was to try icedtea.  I will report back with the result.  Thanks.

---

### Post by Lorin Ricker on 2014-06-02
The Google Chrome/Chromium dev-team no longer supports the Java/IcedTea plugin since Chrome v.35 (Aura):

 [ http://ubuntuforums.org/showthread.php?p=13037595]("http://ubuntuforums.org/showthread.php?p=13037595")

---

