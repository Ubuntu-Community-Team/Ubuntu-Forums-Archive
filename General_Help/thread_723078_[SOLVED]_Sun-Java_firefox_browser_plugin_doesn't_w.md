---
title: "[SOLVED] Sun-Java firefox browser plugin doesn't work"
date: 2008-03-13
forum: General Help
---

### Post by hosammy on 2008-03-13
I have the captioned problem after I upgrade Ubuntu from 6.10 to 7.04 then to 7.10.
In the Firefox browser with Java application, it prompts me to install the missing plugin and I select the "The Java(TM) Plug-in, Java SE6", closed and reopened the firefox, the problem persists that it still prompts me to install the missing Java Plugin.

In a terminal window, I type: java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

I type: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
It replies that I had installed all newest versions.

I type: sudo update-alternatives --config java
and I had selected " /usr/lib/jvm/java-6-sun/jre/bin/java" as default

At the Firefox browser, I type at the url: "about:plugins" and cannot find out the java plugin is working.

Please advise ...

---

### Post by PmDematagoda on 2008-03-13
Please post the output of:-
```
locate javaplugin.so
```

---

### Post by hosammy on 2008-03-13
I type: locate javaplugin.so
Output:
/var/lib/dpkg/alternatives/midbrowser-javaplugin.so
/var/lib/dpkg/alternatives/firefox-javaplugin.so
/var/lib/dpkg/alternatives/iceape-javaplugin.so
/var/lib/dpkg/alternatives/mozilla-javaplugin.so
/var/lib/dpkg/alternatives/mozilla-snapshot-javaplugin.so
/var/lib/dpkg/alternatives/xulrunner-javaplugin.so
/var/lib/dpkg/alternatives/iceweasel-javaplugin.so
/etc/alternatives/midbrowser-javaplugin.so
/etc/alternatives/firefox-javaplugin.so
/etc/alternatives/iceape-javaplugin.so
/etc/alternatives/mozilla-javaplugin.so
/etc/alternatives/mozilla-snapshot-javaplugin.so
/etc/alternatives/iceweasel-javaplugin.so
/etc/alternatives/xulrunner-javaplugin.so
/usr/lib/firefox/plugins/libjavaplugin.so
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/openoffice/program/sunjavaplugin.so
/usr/lib/iceape/plugins/libjavaplugin.so
/usr/lib/mozilla-snapshot/plugins/libjavaplugin.so
/usr/lib/iceweasel/plugins/libjavaplugin.so
/usr/lib/xulrunner/plugins/libjavaplugin.so
/usr/lib/midbrowser/plugins/libjavaplugin.so


Please help ...

---

### Post by ibuclaw on 2008-03-13
you could delete your firefox plugin registry
```
 rm $HOME/.mozilla/firefox/pluginreg.dat 
```

Firefox will create a new one when you restart it, with updated plugin information if it has changed since upgrading.

A small shot in the dark, but worth trying.

Iain

---

### Post by ibuclaw on 2008-03-13
Also, just for reference.

This is my about:config page in firefox. about:config shows all the configurations and settings of the browser. I've used java as a filter so you can see where all my settings point to, so if yours is any different, you could adjust it in accordance (make a backup), and see if it works.

[[IMG]http://img394.imageshack.us/img394/2968/javama0.th.png[/IMG]](http://img394.imageshack.us/my.php?image=javama0.png)

It has some important stuff, such as where is your java location, file versions and library names.

Iain

---

### Post by hosammy on 2008-03-13
I have tried to deleted the "pluginreg.dat" file and restart the firefox but the problem persists.
In firefox, following your instruction to type about : config and the output is similar to yours.

Please advise

---

### Post by hosammy on 2008-03-16
I have tried to remove the other java plugin like the gcj but the problem persists.
I then re-install the gcj & gcj web javaplugin and the "about :plugin" indicates that the java plugin using is the gcj one but not the sun java. However, I need the sun java plugin becasue the web I access are banking webs and they requires the sun java.
The one I access : 
[http://www.standardchartered.com.hk/](http://www.standardchartered.com.hk/)   (the online services)
[http://www.dahsing.com/dsb/rbd/html/index_e.htm](http://www.dahsing.com/dsb/rbd/html/index_e.htm)   (the ebanking login)


Please advise

---

### Post by hosammy on 2008-03-17
I eventually solved my problem after a thorough search of the forum by this thread:
[http://ubuntuforums.org/showthread.php?t=673335](http://ubuntuforums.org/showthread.php?t=673335)

The method is simple:
1. install the newest sun java & its plugin 
2. uninstall the gcj & icetea java
3. type the following: sudo update-java-alternatives -s $(update-java-alternatives -l | cut -d' ' -f1)

Administrator, please mark this thread as "solved"

---

