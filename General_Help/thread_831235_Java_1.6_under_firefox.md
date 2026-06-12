---
title: "Java 1.6 under firefox"
date: 2008-06-16
forum: General Help
---

### Post by rammy1972 on 2008-06-16
I tried installing Sun Java 1.6 using synaptic packages sun-java6-jre and sun-java-plugin and sudo update-alternatives --config java but firefox doesn't run java. On another blog it mentions uninstalling icedteagcj-plugin but it was never installed with java 1.6. I don't have icedtea installed. So what else could be the problem?

---

### Post by avtolle on 2008-06-16
Preliminary question; are you running 32 bit or 64 bit OS? If 64 bit, there isn't a sun plugin to work with FF, and you will need to work with iced-tea, IIRC.

---

### Post by Zorael on 2008-06-16
edit: rampant editorama!

I'll just go ahead and assume you're using 32-bit, while we wait for your response.

First off, I think you want to make sure you have the **sun-java6-plugin** package installed. If you do and it still doesn't work, we'll need to toil with the links to the java plugin library.
```
$ ls -l /usr/lib/mozilla/plugins/*java*
```
With any hope, it links towards [FONT="Courier New"]/etc/alternatives/xulrunner-1.9-javaplugin.so[/FONT]. Example output from my system:
```
$ ls -l /usr/lib/mozilla/plugins/*java*
lrwxrwxrwx 1 root root 45 2008-06-17 00:04 /usr/lib/mozilla/plugins/libjavaplugin.so -> **/etc/alternatives/xulrunner-1.9-javaplugin.so**
```


So, you'll want to pick the xulrunner-1.9-javaplugin.so alternative to use.
```
$ sudo update-alternatives --config xulrunner-1.9-javaplugin.so
```
You want to pick [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so[/FONT]. If it's not there, you'll need to install it:
```
$ sudo update-alternatives --install /etc/alternatives/xulrunner-1.9-javaplugin.so xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so 90
```


Then do the *--config xulrunner* command again. Restart firefox, open up about:plugins and see if Java is mentioned there.

---

### Post by rammy1972 on 2008-06-17
Sorry for the late reply, Itried command
 ls -l /usr/lib/mozilla/plugins/*java*
all I get as a reply is from ls listing any file with the wildcard is
ls: cannot access /usr/lib/mozilla/plugins/*java*: No such file or directory
so it appears not to have installed. which is weird since it is installed as a package in synaptic

---

### Post by Zorael on 2008-06-17
**I'm still assuming you're on a 32-bit installation, by the way.**


First off, make sure you didn't miss **sun-java6-plugin**.

If the symlink is missing, we'll just have to create it. Enter these commands in order. Copied, pasted, reordered and modified from my earlier post:
```
$ sudo ln -s /etc/alternatives/xulrunner-1.9-javaplugin.so /usr/lib/mozilla/plugins/libjavaplugin.so
$ sudo update-alternatives --config xulrunner-1.9-javaplugin.so
```
You want to pick [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so[/FONT]. If it's there to pick, restart Firefox, open up about:plugins and see if Java is mentioned.

*IF* it's not there, you'll need to install it:
```
$ sudo update-alternatives --install /etc/alternatives/xulrunner-1.9-javaplugin.so xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so 90
```
Then do the *--config xulrunner* command again.
```
$ sudo update-alternatives --config xulrunner-1.9-javaplugin.so
```
...then pick it.

---

