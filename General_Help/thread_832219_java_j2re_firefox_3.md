---
title: "java j2re firefox 3"
date: 2008-06-17
forum: General Help
---

### Post by ptrbee on 2008-06-17
Hi can anyone advise how to get Java working?

I'm using Mint Elyssa with firefox 3,kernel 2.6.24-16-generic, j2re is installed but I can't seem to get the java applet working. 

So far I've tried, " sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/xawt/libmawt.so " also tried " sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so ", sudo update-alternatives --config java ", "sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox-3.0/plugins ", "sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox-addons/plugins/", £sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/" and "sudo update-alternatives --config java " all with no joy at all.
Output from alternative shows:-

There are 3 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/jvm/java-6-sun/jre/bin/java
+ 2 /usr/lib/jvm/java-6-openjdk/jre/bin/java
3 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Has anyone else seen this or does anyone know how to fix??

Ptrbee.

---

### Post by samuel_oc on 2008-06-19
Try this:
[http://jpbotelho.info/blog/2008/03/11/java-no-firefox-3/](http://jpbotelho.info/blog/2008/03/11/java-no-firefox-3/)

I didnt find the libjavaplugin_oji.so and havent put it on task so far, but give it a try and post here if you make it.

Bye.

---

### Post by Pjotr123 on 2008-06-19
This is an easy method:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

