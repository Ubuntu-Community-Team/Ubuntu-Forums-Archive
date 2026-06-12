---
title: "How to switch from IcedTea to Sun Java plugin in Firefox under Maverick?"
date: 2013-05-28
forum: General Help
---

### Post by Magnificent 7 on 2013-05-28
Had a scratch around this forum and elsewhere for a day or so, without any success in getting an exact answer to this one.

I'd like to access some work resources written in Java on my personal PC, which at the moment is running 10.10.  I know that the immediate answer to my non-starting Java applet is to do a distribution upgrade to at least 12.04 but for a couple of reasons this isn't immediately practical.

So far I've tracked down how to change the run-time from OpenJDK to the Sun Java 6 that was installed at some time in the past, and that also came with the Sun Java plugin. However Canonical's 2012 update rolled out a patch disabling the Sun plugin and substituting the IcedTea plugin from the OpenJDK.

There are various suggestions for manual changes of path kicking around out there, but I wonder does anyone have a definitive guide for what paths have to be changed in 10.10 within the Firefox profile under ~/.mozilla and elsewhere to point Firefox at the Sun plugin rather than the current IcedTea one?

Any guidance appreciated.

---

### Post by dino99 on 2013-05-28
Maverick have died some times ago  :confused:   [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[http://java.dzone.com/articles/choosing-java-version-ubuntu](http://java.dzone.com/articles/choosing-java-version-ubuntu)

---

### Post by Magnificent 7 on 2013-05-28
> **dino99 said:**
> Maverick have died some times ago  :confused: Mine seems still to be going strong and very much in the land of the living? :confused: although with no updates or support now. Hence the post

> **dino99 said:**
> [http://java.dzone.com/articles/choosing-java-version-ubuntu](http://java.dzone.com/articles/choosing-java-version-ubuntu)Yep found similar references, those re-point the JDK and JRE. I'm asking about the Java plugin, which remained stubbornly pointed at IcedTea despite the update-java-alternatives once-over.

---

### Post by Magnificent 7 on 2013-05-29
At least [one souce]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/288397") I've found recommends searching for symlinks for libjavaplugin.so in the following locations
```
/usr/lib/xulrunner/plugins/libjavaplugin.so
/usr/lib/xulrunner-addons/plugins/libjavaplugin.so
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/firefox/plugins/libjavaplugin.so
```
Of which in my implementation of 10.10 I only have libjavaplugin.so in the third location, with the symlink
```
/usr/lib/mozilla/pluginslibjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
```
which further symlinks to the unwanted IcedTea plugin:
```
/etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
```
On the face of it, it would seem obvious to change the second symlink manually to the Sun Java6plugin
```
/etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun-1.6.0.26/jre/plugin/i386/ns7/libjavaplugin_oji.so
```and in fact one of the posters in the previously referenced source has deleted all the symlinks for libjavaplugin and successfully created a new symlink under $HOME/.mozilla/plugins:
```
ln -s /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/libnpjp2.so
```as he wanted to use Java6 plugin2 in Firefox 3.

However, if I look at my Firefox (2) profile, there is a file called pluginreg.dat containing details of the helper applications including the Java-specific stuff
```
[PLUGINS]
.
.
.
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1329572101000:1:4:$
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.10.1)) executes Java applets.:$
IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.10.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$

etc etc
```
with a message at the top not to edit this automatically generated file.

Question is, is it safe to go ahead and switch the symlinks to point to Sun Java6, in the expectation that pluginreg.dat will be repaired when the new Java plugin library is found when Firefox next loads? Any help/experience appreciated.

---

### Post by ibjsb4 on 2013-05-29
> **Magnificent 7 said:**
> Mine seems still to be going strong and very much in the land of the living? :confused: although with no updates or support now.

You still may be able to get some updates.

[https://help.ubuntu.com/community/EOLUpgrades#Upgrade](https://help.ubuntu.com/community/EOLUpgrades#Upgrade)

---

### Post by Magnificent 7 on 2013-05-29
> **ibjsb4 said:**
> You still may be able to get some updates.

[https://help.ubuntu.com/community/EOLUpgrades#Upgrade](https://help.ubuntu.com/community/EOLUpgrades#Upgrade)

Thanks, but due to some mission-critical stuff that I need still to work for a couple of weeks I can't do a dist-upgrade right now. In any case I'd upgrade from 10.10 to 12.04.x LTS, rather than the options listed. I know that ultimately the answer is to upgrade to a distro with either an up-to-date OpenJDK plugin or Sun Java7, but for the moment I'm looking for pointers from someone who has had to figure out this plugin switchover already for 10.10 or releases around that time.

---

