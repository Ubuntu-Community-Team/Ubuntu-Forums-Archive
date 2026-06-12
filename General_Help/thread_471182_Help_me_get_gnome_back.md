---
title: "Help me get gnome back"
date: 2007-06-11
forum: General Help
---

### Post by floke on 2007-06-11
Have been doing some extensive mucking around on my pc today - mostly installing and removing games etc. Anyhow - for some reason gnome no longer works. When I try to log in all I get is a black screen with my mouse pointer. I can still use KDE perfectly so can log in to that. But some gnome apps don't work - eg f-spot, terminal, system logs (how do I check those in KDE?) etc.

I have tried dpkg-reconfigure gdm; have tried renaming .gnome etc. files, setting up a new user and so on. Also tried different kernels, and am not using beryl.

I managed to get it working temporarily about an hour ago after reinstalling loads of gnome-related stuff, but now for some reason its all gone again. Maybe a shared library issue - but why would it re-break for no apparent reason?

Any thoughts?

** EDIT ** Here's the packages I reinstalled in synaptic to fix it earlier. Some apps - eg synaptic, still work fine 9if that helps)

Commit Log for Mon Jun 11 21:35:24 2007

Installed the following packages:
fast-user-switch-applet (2.18.0-0ubuntu1)
gnome-backgrounds (2.16.1-1)
gnome-core (1:2.14.3.3ubuntu1)
gnome-desktop-environment (1:2.14.3.3ubuntu1)
industrial-cursor-theme (0.6.1.3)

Reinstalled the following packages:
gnome-applets (2.18.0-0ubuntu1)
gnome-applets-data (2.18.0-0ubuntu1)
gnome-desktop-data (1:2.18.1-0ubuntu1)
gnome-keyring (0.8.1-0ubuntu1)
gnome-keyring-manager (2.18.0-0ubuntu1)
gnome-menus (2.18.0-0ubuntu3)
gnome-mime-data (2.4.3-1)
gnome-mount (0.5-2ubuntu8)
gnome-netstatus-applet (2.12.1-0ubuntu3)
gnome-nettool (2.18.0-0ubuntu1)
gnome-panel (1:2.18.1-0ubuntu3.1)
gnome-panel-data (1:2.18.1-0ubuntu3.1)
gnome-power-manager (2.18.2-0ubuntu3)
gnome-session (2.18.0-0ubuntu3)
gnome-system-monitor (2.18.1.1-0ubuntu1)
gnome-terminal (2.18.0-0ubuntu1)
gnome-terminal-data (2.18.0-0ubuntu1)
gnome-utils (2.18.0-0ubuntu2)
gnome-volume-manager (2.17.0-0ubuntu2)
gtk2-engines (1:2.10.1-0ubuntu1)
hwdb-client-common (0.6.10.1)
hwdb-client-gnome (0.6.10.1)
libgail-common (1.18.0-0ubuntu1)
libgail18 (1.18.0-0ubuntu1)
libgconf2-4 (2.18.0.1-0ubuntu1)
libgda2-3 (1.2.4-0ubuntu1)
libgda2-common (1.2.4-0ubuntu1)
libgdl-1-common (0.6.1-1)
libgnome-desktop-2 (1:2.18.1-0ubuntu1)
libgnome-window-settings1 (1:2.18.1-0ubuntu2.1)
libgnomeui-0 (2.17.92-0ubuntu1)
libgnomeui-common (2.17.92-0ubuntu1)
libpanel-applet2-0 (1:2.18.1-0ubuntu3.1)
libxml2 (2.6.27.dfsg-1ubuntu3)
nautilus (1:2.18.1-0ubuntu1)
nautilus-data (1:2.18.1-0ubuntu1)
network-manager (0.6.4-6ubuntu7)
network-manager-gnome (0.6.4-6ubuntu7)
restricted-manager (0.20)
shared-mime-info (0.20-0ubuntu4)

---

### Post by floke on 2007-06-12
bump - just tried reinstalling loads of gnome stuff via synaptic and it doesn't work this time.

---

