---
title: "[SOLVED] Where is the firefox plugin directory?"
date: 2007-12-14
forum: General Help
---

### Post by DugieHowsa on 2007-12-14
I am running Gutsy (7.10), and am trying to troubleshoot a problem with a firefox plugin.  I am running into trouble as there appears to be multiple firefox (and mozilla) plugin directories.  Which one does Firefox 2.0.0.11 on Gutsy (Ubuntu 7.10) use?

Is it:

~.mozilla/firefox
 or
/etc/alternatives ( there are a bunch of firefox- and  mozilla- plungin links here)
 or
/usr/lib/mozilla/plugins
 or
/usr/lib/firefox/plugins

If one of these directories is the true plugin directory, what are these other directories for?

---

### Post by aysiu on 2007-12-14
The ~/.mozilla/firefox one would be plugins available to only one user.

I believe /usr/lib/firefox/plugins is the correct plugin directory to use.

---

### Post by DugieHowsa on 2007-12-15
Interesting.  So I checked there to confirm that there is a link to the plugin, and there is:

```

user@Ubuntu:/usr/lib/firefox/plugins$ ls -la
drwxr-xr-x 2 root root 4096 2007-12-07 22:33 .
drwxr-xr-x 5 root root 4096 2007-12-06 20:22 ..
lrwxrwxrwx 1 root root   52 2007-08-18 10:34 libjavaplugin_oji.so -> /usr/local/java/plugin/i386/ns7/libjavaplugin_oji.so

```

The link is executable by all, and so is the plugin:
```

user@Ubuntu:/usr/lib/firefox/plugins$ ls -la /usr/local/java/plugin/i386/ns7/ 
drwxr-xr-x 2 root root 4096 2007-06-14 21:02 .
drwxr-xr-x 4 root root 4096 2007-06-14 21:02 ..
-rwxr-xr-x 1 root root    0 2007-12-02 11:13 libjavaplugin_oji.so

```

The about:plugins page in firefox seems to indicate that the plugin is installed:
```

Java(TM) Plug-in 1.6.0_03-b05
File name: libjavaplugin_oji.so
Java(TM) Plug-in 1.6.0_03

```
So why is it that when I go the java verification page, it does not detect the plugin?
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

---

### Post by SunnyRabbiera on 2007-12-15
I think that java checker only checks for newer versions of java as I installed java 6 and it works.
anyhow most of the time the firefox plugins are located in either usr/lib/firefox/plugins, usr/lib/mozilla/plugins or sometimes even usr/lib/navigator/plugins.

---

### Post by DugieHowsa on 2007-12-15
According to the about:plugins page, I have the latest version installed.

I found another test page, and this one with list the version that is installed.  Except for me, it doesn't work.

[http://www.javatester.org/version.html](http://www.javatester.org/version.html)

I confirmed that java is installed, but this tells nothing about the plugin.
```

user@Ubuntu:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

I checked the mozilla directory, and the plugin linked there is the same:
```

user@Ubuntu:/usr/lib/mozilla/plugins$ ls -la
drwxr-xr-x 2 root root 4096 2007-12-07 22:37 .
drwxr-xr-x 3 root root 4096 2007-04-15 07:53 ..
lrwxrwxrwx 1 root root   52 2007-12-07 22:36 libjavaplugin_oji.so -> /usr/local/java/plugin/i386/ns7/libjavaplugin_oji.so

```

Any more thoughts on how to further troubleshoot this problem?

---

### Post by DugieHowsa on 2007-12-15
Finally... it looks like everything is now working.

First, I went to the about:config page in firefox and set the following value to true:

plugin.expose_full_path

Next, I went back to the about:plugins page in firefox.

Upon further review, I found that I had 2 instances of java plugins, both trying to execute from different directories.

The official Ubuntu sun-java6 binaries are installed in /usr/lib/jvm . I deleted the other java directory from my machine.

I then confirmed that all the java plugin links were pointing to the remaining java plugin binary.  This included the following:

```

/usr/lib/mozilla/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/usr/lib/firefox/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Finally, I restarted firefox, and went back to the about:plugins page to confirm there was only one instance of the java plugin installed.  Upon revisting the Java test pages, the java plugin was recognized successfully.

---

