---
title: "Automatic login not working, can't disable sleep unlock requirement"
date: 2015-01-30
forum: General Help
---

### Post by Dave_Netz on 2015-01-30
I have Ubuntu 14.04 LTE on VirtualBox (Windows 7 64-bit), and my username (the only one) is the administrator, and I have automatic login turned on in settings but it always asks me to type in a password when booting up or waking it from sleep. How do I disable the password request for these two things? I already lock my PC and I only use the virtual box for testing commands, so there's nothing worth losing on it.

---

### Post by kerry_s on 2015-01-31
tweaks-> desktop-> lock screen, set mode: none

---

### Post by Dave_Netz on 2015-02-02
> **kerry_s said:**
> tweaks-> desktop-> lock screen, set mode: none

I'm not sure what you mean by tweaks -> desktop, but I found Settings > Brightness & Lock, which let me turn off inactivity lock and disable require password, but I don't think that's the same as the initial bootup login screen.

---

### Post by kerry_s on 2015-02-02
your using normal ubuntu?
there should be a tweak tool, the other way to get at the setting is using dconf-editor.

i'm on debian gnome, but it has the exact same tools i used in unity, just without all that corporate crap.

---

### Post by Dave_Netz on 2015-02-02
I said what I was using: Ubuntu 14.04 LTE on VirtualBox (Windows 7 64-bit). There's nothing special about it, it's all the default options. It doesn't say Debian at the top left, it says Ubuntu Desktop.

---

