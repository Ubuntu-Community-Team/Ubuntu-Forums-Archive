---
title: "Startup Aplications don't show panel icon"
date: 2021-04-02
forum: General Help
---

### Post by AllesMeins on 2021-04-02
I'm having problems setting up the autostart of some applications properly. As far as I know the "offical" way is via the startup-applications tool. But I've some applications that automatically minimize into an icon in the top panel bar (for example "nextcloud" or "barrier"). This works fine if I start those apps manually thru the launcher or the terminal. But if I add them to the startup programs they get started in background and do not show up in the top panel so i've no way of accessing them. Is this a known problem? And what is the best way to launch a program at startup and make sure it can create the panel-icon?

I'm using Ubuntu 20.04 LTS with all the current Updates.

---

### Post by ActionParsnip on 2021-04-02
Is there an option on the application binary to go to tray etc?

---

### Post by AllesMeins on 2021-04-02
I don't think so - at least it isn't nescessary when launching the binaries from Terminal

---

### Post by dragonfly41 on 2021-04-02
[Stacer]("https://linuxconfig.org/how-to-install-stacer-on-ubuntu-20-04-focal-fossa-linux-desktop") has a useful GUI for launching apps at startup. And other features for management.

---

### Post by AllesMeins on 2021-04-02
Unfortunately stacer seems to access the same startup-routine as "startup programs". So my apps are already there and don't behave any differently when launched with stacer.

---

