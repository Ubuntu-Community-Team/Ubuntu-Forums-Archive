---
title: "Upgraded to Edgy, installed Beryl, LimeWire no longer launches"
date: 2007-02-26
forum: General Help
---

### Post by rainwalker on 2007-02-26
I just upgraded to Edgy from Dapper a couple of days ago, installed Beryl (which is working fine), but I just tried launching LimeWire and nothing happens. I know I have the latest version of Java installed, "java -version" gives me this:
> java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

I have no idea what to do, but I haven't tried FrostWire to see if it works (I uninstalled it before upgrading to Edgy).

---

### Post by m.musashi on 2007-02-26
Yep. Limewire doesn't seem to work if beryl is running. Try exiting beryl and just running limewire. You might need to ctrl-alt-backspace to get beryl unloaded.

---

### Post by rainwalker on 2007-02-26
It didn't work, the screen faded into this wierd whiteness, logged off, and after logging back in everything is the same (even though I set it to use Metacity).

---

### Post by m.musashi on 2007-02-26
Is beryl auto loading? Even if set to metacity but beryl is loaded it may not work. I seem to recall trying to turn off beryl that way and run limewire but it only worked when beryl was fully off. I think you can also kill beryl by doing
```
sudo killall beryl-manager
```
but that might not work either. Maybe it's a different command. Just log out and don't auto load it and then try.

---

