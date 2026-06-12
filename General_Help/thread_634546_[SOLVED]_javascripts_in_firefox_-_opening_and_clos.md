---
title: "[SOLVED] javascripts in firefox - opening and closing pages"
date: 2007-12-07
forum: General Help
---

### Post by DugieHowsa on 2007-12-07
Has anyone else noticed an issue with java scripts running in firefox 2.0.0.11 with the Java 6 plug-in?  I have been noticing this behavior since upgrading to Gutsy (7.10).

At first, I was just having the problem with my bank's web site.  When it tried to execute a java script to redirect to an https web site, it timed out.  The rest of the java scripts worked fine, but they pertained mostly to just site searches.

Then all of a sudden, I found a similar problem when I was filling out an on-line survey.  At the end, it had a java script for closing the window.  That script failed to execute as well.

My question is as follows:  Does firefox have some security setting that disables certain java functions?  I've tried enabling all the Javascript options in the Preferences -> Content, but there is nothing there about opening and closing pages, just actions such as resizing the window and hiding the status bar (among other things).

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
One more thing I noticed:

Problem solved. I was running peergaurdnf ([http://sourceforge.net/projects/moblock-deb](http://sourceforge.net/projects/moblock-deb)). As soon as I killed that process the javascripts redirecting to https worked in all browsers. I also removed the link from the /etc/init.d directory so it will no longer start automatically on startup.

NOTE:  Javascript and Java are two completely different things.  This was a very important lesson I learned through this process.  Javascript engines are embeded as part of the browsers.  Java Runtime Environments require a java-plugin.  You can actually run javascript with out having the a java-pluging installed.

---

