---
title: "java problems in firefox 3"
date: 2008-07-02
forum: General Help
---

### Post by boxercbuk on 2008-07-02
recently un and reinstalled hardy heron and am now having problems in firefox  with java and also video feed playback some java scripts load and work fine most just hang any suggestions as what to do would be appreciated 
cheers
steve

---

### Post by scouser73 on 2008-07-02
Look for Sun Microsystems 6JRE in the repos.

---

### Post by imjscn on 2008-07-02
I enabled all the sources, but couldn't search out the Sun Microsystems 6JRE . could you give the exactly name? I installed sun-java6-jre, it's not working.

---

### Post by sultanoswing on 2008-07-02
> **boxercbuk said:**
> recently un and reinstalled hardy heron and am now having problems in firefox  with java and also video feed playback some java scripts load and work fine most just hang any suggestions as what to do would be appreciated 
cheers
steve

Yeah - me too. I'm using the repository installed sun-java6-plugin and sun-java6-jre (etc.) on Hardy Heron (32-bit) under Firefox 3.0 and also Swiftfox (3.0 and 3.01 pre) and get errors on some java test pages:

[http://www.bodo.com/javame.htm](http://www.bodo.com/javame.htm) - *WARNING MAY CRASH YOUR BROWSER*

While others (the official one) run fine:

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

Curious!

---

### Post by scouser73 on 2008-07-02
> **imjscn said:**
> I enabled all the sources, but couldn't search out the Sun Microsystems 6JRE . could you give the exactly name? I installed sun-java6-jre, it's not working.

Sorry for not pasting the exact details that you needed the first time.

It is; **sun-java6-jre** & **sun-java6-plugin**.

I hope that this is a bit more useful than my last posting.

---

### Post by imjscn on 2008-07-02
thanks!
I think there's something wrong in firefox3 newest updating. sun-java6-jre alone can work before. it's just not working today. and I lost my all bookmarks by restarting firefox after install google notebook extention. strange day.

---

### Post by jamesstansell on 2008-07-03
To enable the sun java plugin in firefox 3 on hardy, this should work.
```
sudo apt-get remove icedtea-gcjwebplugin && sudo apt-get install sun-java6-plugin && sudo update-java-alternatives -s java-6-sun
```

---

### Post by Bubba64 on 2008-07-03
[http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive](http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive)

---

### Post by rockets on 2009-01-07
I am running Hardy Heron and Firefox 3. My system has multiple locations for browser plugins. Read that again: MULTIPLE. Not links, COPIES. Of all the locations I found, only this one was the one that positively fixed the problem:

/usr/lib/xulrunner-addons/plugins

To that location I linked the Sun Java 6.04.xxxx browser plugin and eveything worked PERFECT. In my system, the command was:

sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/xulrunner-addons/plugins/libjavaplugin_oji.so

Restarting Firefox and typing **about : plugins** as the URL revealed the correct presence of the Java plugin.

Why all the locations (/usr/lib/iceweasel/plugins, /usr/lib/mozilla/plugins ....) in Hardy? Beats me.

Hopefully this is useful for the next soul searching the web.

---

