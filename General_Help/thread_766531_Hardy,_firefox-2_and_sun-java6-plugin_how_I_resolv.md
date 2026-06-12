---
title: "Hardy, firefox-2 and sun-java6-plugin how I resolved it"
date: 2008-04-25
forum: General Help
---

### Post by Jelloir on 2008-04-25
I don't know if this was just me but I thought I would post this in case anyone else has this problem.

I'm running Kubuntu 8.04 and installed firefox-2 (rather than 3) and sun-java6-plugin for Java stuff on the Web but Java would not work and sites using it kept prompting to install the plugin.

Eventually after some googling I figured out that I needed a link to the java plugin in Firefox's plugin directory as it was missing.

```
sudo ln -s /etc/alternatives/xulrunner-1.9-javaplugin.so /usr/lib/firefox/plugins
```

Restarted Firefox 2 and now it works.

Hope it helps someone else

---

### Post by lns on 2008-09-17
Wow, thank you!! Worked like a charm in Ubuntu 8.04.1 w/Firefox-2 installed.

:guitar:

---

