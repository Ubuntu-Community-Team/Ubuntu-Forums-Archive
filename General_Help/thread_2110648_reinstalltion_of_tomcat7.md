---
title: "reinstalltion of tomcat7"
date: 2013-01-30
forum: General Help
---

### Post by rwharper on 2013-01-30
I am trying to reinstall tomcat7 on my ubuntu 12.04 device.  The installation continues to fail.  How can I completely remove all traces of it and reinstall?
Thanks

---

### Post by Bashing-om on 2013-01-30
rwharper; Hi !

If you installed tomcat7 through ubuntu's package management system, This should do the trick: Terminal codes:
```

sudo apt-get purge tomcat7
sudo apt-get install tomcat7
```see ```
man apt-get
``` for detailed explanation.
[INDENT][INDENT]hth
 
[/INDENT][/INDENT]

---

### Post by rwharper on 2013-02-04
Thanks!  That works.  However, now it fails to install claiming 'no JDK found - please set JAVA_HOME'.  I have set JAVA_HOME (/usr/lib/jvm/java-7-oracle) to an installed JDK.  The installer does not seem to recognize it.  I also tried setting a symbolic link from /usr/bin/java to the jdk (as some suggested) that did not work either.  Any ideas as to how to get the jdk recognized?

Thanks again

---

