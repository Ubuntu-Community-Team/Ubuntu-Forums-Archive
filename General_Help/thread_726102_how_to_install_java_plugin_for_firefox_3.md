---
title: "how to install java plugin for firefox 3?"
date: 2008-03-16
forum: General Help
---

### Post by robertchahine on 2008-03-16
i have installed sun java 6 from the add/remove list.
but when i'm working on the firefox 3 , it still telling me that the java plugin is missing? what to do?

---

### Post by Ub1476 on 2008-03-16
I would use this guide to install Firefox3 with plugin support like Firefox2:
[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html]("http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html")

You have to change the beta file name though. Probably only making a symbolic link from Firefox2 plugin directory to Firefox3 plugin directory will do just as fine though.

---

### Post by robertchahine on 2008-03-16
i'm using firefox 3 beta 4.
and followed the instructions of the url that you gave me.

---

### Post by d3mia7 on 2008-03-19
On Hardy, if you want the "closest thing" to how it SHOULD be set up, do this:

ln -s  /etc/alternatives/firefox-javaplugin.so /usr/lib/firefox-addons/plugins/libjavaplugin.so

Then restart firefox...

MUCH better than moving all kinds of things around all over the place...  Oh yeah, I'm assuming you actually HAVE a browser plugin installed on your system in the first place for this to work!  The previous poster's instructions tell you to create a totally new Firefox installation, which probably isn't what you want (nor is it required)

---

### Post by robertchahine on 2008-03-21
isn't the java 6 web starter in the add/remove list , a plugin for firefox 3.?

---

### Post by d3mia7 on 2008-03-24
The plugin is included with Hardy, however Firefox 3 on Hardy currently isn't loading anything in /usr/lib/firefox-addons/plugins directory.  It IS however loading plugins from /usr/lib/firefox-3.0b4/plugins

I'm sure this is just a "temporary" thing and will get fixed soon enough, but in the meantime a quick symlink takes care of things.  This should work for just about any plugin btw, not just java...

---

### Post by yoel.koenka on 2008-06-25
Hello,
I tried making the link and then found out that the file "/etc/alternatives/firefox-javaplugin.so" doesn't exist in my system.
Can someone tell me where it comes from?
10x
Yoel

---

