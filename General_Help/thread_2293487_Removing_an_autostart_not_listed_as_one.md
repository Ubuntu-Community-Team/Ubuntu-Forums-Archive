---
title: "Removing an autostart not listed as one"
date: 2015-09-05
forum: General Help
---

### Post by Exacom on 2015-09-05
Hello ubuntu-Community,

A while ago I have installed the voice-over-IP client Mumble over the Ubuntu Software Center. After I marked "Save session for future logins" one time I shut down the computer, Mumble now starts automatically everytime the PC is started from a complete shutdown. There is no Mumble-related file (I could remove) in ~/.config/autostart , neither did I ever create an autostart for any program intentionally. Mumble itself has no functionality in that sense in its menus, and a "Complete Removal" and Reinstallation via Synaptic Package Manager didn't do anything aswell.

Thank you in advcance ;)

---

### Post by ajgreeny on 2015-09-05
Go to "Sessions and startup" in the Settings-manager and **Clear saved sessions** then logout of the session but make sure the tick box for Save session is not selected in the logout dialogue.

Hopefully the unwanted Mumble will now not start every time you login.

---

