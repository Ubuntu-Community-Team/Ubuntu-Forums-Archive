---
title: "[SOLVED] Troubleshooting Java in Firefox"
date: 2007-12-02
forum: General Help
---

### Post by DugieHowsa on 2007-12-02
I realize this may be outside the the  context of this forum, so if some one could point me in the right direction I would appreciate it.

I am having trouble accessing my on-line bank in Firefox.  I have determined that it has to do with the JRE, as the initial page re-direction is done in java.

I can reach the page with out issue on other computers, so I know its not on their end and its on mine,

I am 95% certain that i have the jre installed correctly, because:

1)  when I issue the about:plugin command in firefox it show that it is installed and enabled.
2)  the java verification page at java.com recognizes the latest version is installed.

The 5% that makes me uncertain it is installed correctly is that it seems java is installed in multiplelocations on my host:

```

/usr/local/java/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Does it matter which one it is using?

---

### Post by jken146 on 2007-12-02
Do you have anything in Firefox that blocks Javascript?

---

### Post by DugieHowsa on 2007-12-02
Not to my knowledge.  I would have to say No since the java verify page at java.com appears to work.  In Firefox -> Edit -> Preferences -> Content, Both Enable Javascript and Enable Java are checked.  I also have all the boxes checked under Enable javascript (for now, for trouble shooting purposes.

One thing I noticed is that I do not have a ~/.mozilla/firefox/plugins directory.  Is that a probelm?

What is the difference between libjavaplugin_oji.so and libjavaplugin.so?

In the /etc/alternatives directory, what is the difference between the firefox-javaplugin.so link and the mozilla-javaplugin.so link?

I did find the pluginreg.dat file in my ~/.mozilla/firefox directory.  Is this a configuration file, or does this just register what has been configured so far?

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

### Post by DugieHowsa on 2008-01-11
Problem solved. I was running peergaurdnf ([http://sourceforge.net/projects/moblock-deb](http://sourceforge.net/projects/moblock-deb)). As soon as I killed that process the javascripts redirecting to https worked in all browsers. I also removed the link from the /etc/init.d directory so it will no longer start automatically on startup.

NOTE:  Javascript and Java are two completely different things.  This was a very important lesson I learned through this process.  Javascript engines are embeded as part of the browsers.  Java Runtime Environments require a java-plugin.  You can actually run javascript with out having the a java-pluging installed.

---

