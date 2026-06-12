---
title: "Cannot install JRE in firefox"
date: 2007-05-14
forum: General Help
---

### Post by kbneo on 2007-05-14
I just switched from windows and install ubuntu 7.04, Firefox 2. I had downloaded the jre file and unpacked in /usr/java.  cd to /usr/lib/firefox/plugins and ln -s /usr/java/jrel6.0_01/plugin/i386/ns7/libjavaplugin_oji.so.  restarted firefox and it didn't work. I also try to link to /usr/lib/mozilla-firefox/plugins.  The links at both locations always shown broken.  Anyone please help ?  Thanks.

---

### Post by dcstar on 2007-05-15
> **kbneo said:**
> I just switched from windows and install ubuntu 7.04, Firefox 2. I had downloaded the jre file and unpacked in /usr/java.  cd to /usr/lib/firefox/plugins and ln -s /usr/java/jrel6.0_01/plugin/i386/ns7/libjavaplugin_oji.so.  restarted firefox and it didn't work. I also try to link to /usr/lib/mozilla-firefox/plugins.  The links at both locations always shown broken.  Anyone please help ?  Thanks.

Install the** j2re1.4-mozilla-plugin** package.

---

### Post by kbneo on 2007-05-15
Thank you, David. Installed and is working.

---

