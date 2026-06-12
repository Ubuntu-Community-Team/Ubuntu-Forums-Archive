---
title: "(Gnome Control Center) Sytem Settings (4 Day Old Install)"
date: 2023-03-07
forum: General Help
---

### Post by sonicdiscovery on 2023-03-07
System setting will not open.

Is there a way to fix this? I have tried many things with no luck, short of a fulll reinstall. Thank you :)

error: XDG_RUNTIME_DIR not set in the environment.

(gnome-control-center:709165): Clutter-CRITICAL **: 09:59:47.143: Unable  to initialize Clutter: Unable to initialize the Clutter backend: no  available drivers found.

(gnome-control-center:709165): dconf-WARNING **: 09:59:47.184: failed to  commit changes to dconf: Failed to execute child process &#8220;dbus-launch&#8221;  (No such file or directory)
Error creating rfkill proxy: (null)
Segmentation fault

---

### Post by sonicdiscovery on 2023-03-07
.

---

### Post by sonicdiscovery on 2023-03-07
.

---

### Post by Dennis N on 2023-03-07
You could start it from the terminal, but why do this?  If you do, don't use sudo in the command.
You can open the settings dialog from the quick menu (see screenshot) or just type "Settings" in the Activities Overview.

---

### Post by sonicdiscovery on 2023-03-07
Yes, thank you. I should have advised that. I do normally from quick menu and/or activities overview, but both did not work and i got the Gnome crash report window. Then opted for trying to run though the terminal. Thank you

---

### Post by sonicdiscovery on 2023-03-07
Solved by reinstalling Ubuntu. Ubuntu is a fast OS Distro but learning the the hard way of security trade offs with snaps vs .debs, permissions, and drivers. I have a Pro subscription and have been reading the support docs. Might go back to Debian, still trying through.

---

