---
title: "Java Installation for Opera"
date: 2005-08-26
forum: General Help
---

### Post by cymoril on 2005-08-26
Hi there,

I'm having trouble getting Java to work with my browser.

After doing dpkg -i on the .deb I downloaded Java has worked fine with Mozilla Firefox. No such luck with Opera though.

Looking in /usr/lib/mozilla-firefox/plugins I found a link that pointed to /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

I then made a link to libjavaplugin_oji.so in my /usr/lib/opera/plugins directory but that didn't seem to help.

I hava Java enabled in my Opera preferences and my Java path under Java options is  /usr/lib/j2re1.5-sun/plugin/i386/ns7/

When I clicked on "Validate Java Path" though, the program said it couldn't find a valid Java installation.

I don't suppose creating the link did anything as Opera couldn't detect any new plugins either.

Please help.

Thanks,
Cymoril.

---

### Post by wvslkr on 2005-08-26
My working Java path     /usr/lib/j2re1.5-sun/lib/i386.

---

### Post by cymoril on 2005-08-27
thank you.

setting that path and creating a link in opera's plugin directory to libjavaplugin in mozilla's plugin directory fixed the problem.

cym.

---

### Post by cowb0y on 2005-09-01
Newer versions of Opera use Java directly, not the plugin. Make sure the java-common package is installed. See the Opera article  [here](http://www.opera.com/support/search/supsearch.dml?index=459)

---

