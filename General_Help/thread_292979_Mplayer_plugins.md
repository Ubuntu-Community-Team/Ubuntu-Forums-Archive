---
title: "Mplayer plugins"
date: 2006-11-04
forum: General Help
---

### Post by lemonsCC on 2006-11-04
I am trying to setup FF so that it only uses mplayer plugins.  Right now it uses totem and they work some times and not others.  It there any way to disable totem-plugins and enable mplayers?

---

### Post by rudiz on 2006-11-04
1)cd /usr/lib/firefox/plugins/

2)remove all libtotem

---

### Post by jocko on 2006-11-04
I had the same problem. I wanted firefox only to use mplayer and never totem. Uninstalling the totem plugin will remove the meta package ubuntu-desktop, which I want to keep. The only way I could come up with was to move all libtotem- files from /usr/lib/mozilla/plugins/.

I think these are the commands I used:
```
sudo mkdir /usr/lib/mozilla/pluginsbak
sudo mv /usr/lib/mozilla/plugins/libtotem*.* /usr/lib/mozilla/pluginsbak
```
(This way the totem plugin files are moved to the new directory /usr/lib/mozilla/pluginsbak and will not be used. One problem is if the totem plugin is updated, it will become active again)

---

