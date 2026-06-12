---
title: "PLugins for Firefox"
date: 2005-09-20
forum: General Help
---

### Post by facefur on 2005-09-20
I successfully installed Firefox on 5.04, but when I hit a page that needs applet suppport, it keeps asking to install the plugin.  I have already installed the JRE 1,5, or at least I thought I did, but Firefox can't seem to find or use it?

How do I tell if Java is there, and if so, how do I tell Firefox where it is?

---

### Post by Leif on 2005-10-08
if java is installed, doing "sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins" should fix the problem

---

