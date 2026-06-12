---
title: "Unity or Compiz or something is broken"
date: 2012-12-14
forum: General Help
---

### Post by Hungry Man on 2012-12-14
12.10. Everything was fine when I rebooted and my UI wouldn't start up.

So I reinstalled Ubuntu from scratch. All's well, I update everything and use the update-manager to move to fglrx-updates. Reboot - UI is broken.

Trying to move back to the OSS drivers but it just sits at "Applying changes...".

# unity
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Error: Another window manager is already running on screen: 0
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

I managed to go back to the OSS drivers after reformatting (millionth time). So I guess an update was pushed and it really screws things up.

---

