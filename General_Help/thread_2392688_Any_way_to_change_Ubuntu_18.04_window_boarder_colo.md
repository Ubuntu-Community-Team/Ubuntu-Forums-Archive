---
title: "Any way to change Ubuntu 18.04 window boarder colors?"
date: 2018-05-24
forum: General Help
---

### Post by wallacegalloway on 2018-05-24
I'm using the Adwaita theme and would prefer a blue or black border..anything other than orange. I'm trying to recreate a simple vanilla gnome desktop.

---

### Post by monkeybrain20122 on 2018-05-24
Probably gtk-theme-config

It is not in 18.04s repo, so just grab the .deb for artful from [launchpad]("https://launchpad.net/ubuntu/+archive/primary/+files/gtk-theme-config_1.2.2-1_amd64.deb") and install it.

---

### Post by leunam12 on 2018-05-25
Install the Gnome Tweak Tool and change the GTK theme.

---

### Post by again? on 2018-05-25
> **wallacegalloway said:**
> I'm using the Adwaita theme and would prefer a blue or black border..anything other than orange. I'm trying to recreate a simple vanilla gnome desktop.
Install gnome-session...
```
sudo apt install gnome-session
```

Reboot and choose "Gnome on Xorg" at the greeter.
Use gnome-tweaks to enable the Ubuntu dock extension.

---

