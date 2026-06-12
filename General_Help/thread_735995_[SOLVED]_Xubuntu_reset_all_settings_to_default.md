---
title: "[SOLVED] Xubuntu reset all settings to default"
date: 2008-03-26
forum: General Help
---

### Post by Rytron on 2008-03-26
Is there a terminal command to reset all settings to default?
This can be handy if it was required in the future.
Thanks.

---

### Post by justleen on 2008-03-26
what settings are you thinking of?

most can be reconfigured, with dpkg-reconfigre <packagename>

if you mean your X settings, you could delete the /home/user/.gconf and /home/user/.gnome* folders

yet another option woul be to create a new "blank" user. then you could rename you old home, and copy the test-home to your username - mind the ownership though, that would have to be changed.

---

### Post by mali2297 on 2008-03-26
To move all your personal configuration files to a backup folder, use
```

mkdir backup
mv -v \.??* backup

```
That should reset your personal settings but not the system-wide.

---

### Post by Rytron on 2008-03-26
I refer to the settings that are in place when a fresh install of Xubuntu occurs
How to get these settings (without a fresh install / reinstall)?

:)

---

### Post by markharding557 on 2008-03-26
> **Rytron said:**
> I refer to the settings that are in place when a fresh install of Xubuntu occurs
How to get these settings (without a fresh install / reinstall)?

:)

already been said create anew user,new user will have default settings with no reinstallation

---

