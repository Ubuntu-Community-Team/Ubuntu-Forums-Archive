---
title: "Java not working with FireFox 2 - No help from other posts"
date: 2008-06-12
forum: General Help
---

### Post by Lloyd7703 on 2008-06-12
I have a problem with Java 1.6 working with Firefox 2 as many other people on this forum have. Unfortunately it looks like everyone else's problems were fixed by linking the java plugin file:

ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/

This has seemed to fix everyone elses problems but mine. All of my applications (including the version detector at [www.java.com](www.java.com)) show my version as 1.4. But if you do the "about:plugins" in the Firefox browser, it says 1.6.0_03-b05 and shows the correct file linked above. I have uninstalled and re-installed several times. Running a java -version from the command line also shows the Java version 6. I can not seem to find where Firefox is getting this 1.4 version from. I am desperate for help as I have spent many hours scouring through forum posts and trying different suggestions. So far none of them have helped. Any ideas are welcome.


Isaac

---

### Post by Het Irv on 2008-06-12
I am not positive, but 1.6.0_**03-b05** sounds like you have the plugin for Firefox 3 beta 5.  Try this: [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=j2re-1.4.2_17-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=j2re-1.4.2_17-oth-JPR@CDS-CDS_Developer)

Or you could update to Firefox 3, it is going to be released Tues.

---

