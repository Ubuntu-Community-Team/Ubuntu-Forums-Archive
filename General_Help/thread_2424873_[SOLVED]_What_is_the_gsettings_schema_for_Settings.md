---
title: "[SOLVED] What is the gsettings schema for Settings &gt; Universal Access &gt; Sounds Keys"
date: 2019-08-16
forum: General Help
---

### Post by sudoranger on 2019-08-16
I'm using Ubuntu 19.04 and currently trying to enable the sound keys from a command line but not sure where to look for the schema. At first, I thought it was gsettings set org.gnome.desktop.sound event-sounds "true" but I don't think that was it. I've tried to browse for it throughout dconf-editor but still has no idea where it's at; not to mention googled for the information many times. Thanks in advance!

If you plan to answer it on askubuntu, [you can do so here]("https://askubuntu.com/questions/1164116/what-is-the-gsettings-schema-for-settings-universal-access-sounds-keys").

Edit: Changed the title to [SOLVED]

---

### Post by Dennis N on 2019-08-16
Use the Settings Dialog, not dconf-editor:
Settings > Universal Access > Seeing> Sound Keys > On/Off

To find Settings Dialog, type 'Settings' in overview screen search.

---

### Post by cruzer001 on 2019-08-16
```
gsettings list-recursively | grep -i sound
```

Looks like no gsetting available.

---

### Post by deadflowr on 2019-08-16
It's the a11y settings.
Specifically it's org.gnome.desktop.a11y.keyboard togglekeys-enable.

---

### Post by sudoranger on 2019-08-16
The previous dude who replied about Settings Dialog obviously didn't read my post...

> **deadflowr said:**
> It's the a11y settings.
Specifically it's org.gnome.desktop.a11y.keyboard togglekeys-enable.

Hey, man! Thanks so much for this.  I've been looking for this more than a week now and finally found it.

---

