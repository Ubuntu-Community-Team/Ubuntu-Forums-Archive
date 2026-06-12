---
title: "Getting Firefox to use mplayer instead of totem for .wmv"
date: 2007-08-30
forum: General Help
---

### Post by 999alfred on 2007-08-30
I have mplayer and the win32 codecs and mplayer plugin installed. However, when I try to to stream a wmv video it queries if I want to use totem, browse or save to file wants to use totem. I want it to default to mplayer.  When I check  download actions there is not even an action listed for wmv. Plus it does not allow me to add a type, I can only delete or  change an action. I find that according to about:plugins mplayerplug-in 3.31 is there for wmv files.

So, how do I get Firefox to use mplayer plugin for wmv????

tj

---

### Post by ThrobbingBrain66 on 2007-08-31
Totem takes precedence over Mplayer in Firefox.  I've found the easiest way to fix this is to remove the plugin:
```
sudo apt-get remove totem-mozilla
```

---

