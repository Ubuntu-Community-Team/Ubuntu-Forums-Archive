---
title: "Help installing java plugin for Firefox"
date: 2006-07-07
forum: General Help
---

### Post by endokrin on 2006-07-07
Hi.

I have installed JRE via Automatix.
But it appears the plugin isn't working for Firefox.

I have JRE installed:
```

$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

```

I tried:

```

~$ sudo apt-get install sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate

```

```

$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

What's up?

---

### Post by vem0m on 2006-07-07
u have to open ur apt-get to multiverse repositories then u should be able to install it

---

### Post by FredB on 2006-07-08
Automatix problems again ?!

Anyway, you have java installed, which is a good point.

After that, you will have to do a symbolic link from  the  " /etc/alterna tives/firefox-javaplugin.so" to your firefox profile plugin directory.

After closing firefox, open a terminal, and type this :

```

cd .mozilla/plugins/

``` 
You should have this directory.

After this, you have to make a symbolic link.

so type :

```

ln -s  libjavaplugin.so /etc/alternatives/firefox-javaplugin.so
``` 
Launch again firefox, type "about : plugins"  (without the quotes and the spaces between about and : and plugins) in url bar, and you'll get something like this in the list :

> Java(TM) Plug-in 1.5.0_06-b05
 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.5.0_06Hope I helped.

---

