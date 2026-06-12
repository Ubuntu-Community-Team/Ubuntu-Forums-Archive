---
title: "Last update took out my mouse"
date: 2020-06-07
forum: General Help
---

### Post by JamButty on 2020-06-07
The last update, installed an hour ago, appeared to include BIOS updates as I got the loading bar display while in BIOS on reboot, which never appears otherwise. After that boot my mouse was completely non-functional. (Logitech Wireless Trackball M570). Tried with multiple reboots with two different M570s, even on the Windows side and zip.
Now working with basic wired mouse. If I had just one mouse I might assume it broke right at that moment, but two M570s on two OSs right after a BIOS upgrade? Nope.
I assume I can back out of that upgrade, but I don't know how and am unsure if backing out of the BIOS upgrade is possible.
Upgrade happened through standard automatic update process. Here is the pertinent history.log output. I note it included "network-manager-config-connectivity-ubuntu:amd64 " Could that mess with wireless mice?

Is this repairable?
```
Start-Date: 2020-06-07  11:22:36
Commandline: aptdaemon role='role-commit-packages' sender=':1.104'
Upgrade: gir1.2-nm-1.0:amd64 (1.22.10-1ubuntu1, 1.22.10-1ubuntu2.1), gnome-logs:amd64 (3.34.0-1, 3.34.0-1ubuntu1), xserver-common:amd64 (2:1.20.8-2ubuntu2, 2:1.20.8-2ubuntu2.1), xserver-xorg-core:amd64 (2:1.20.8-2ubuntu2, 2:1.20.8-2ubuntu2.1), libgamemode0:amd64 (1.5.1-0ubuntu3, 1.5.1-0ubuntu3.1), gnome-desktop3-data:amd64 (3.36.2-0ubuntu1, 3.36.2-0ubuntu2), gamemode:amd64 (1.5.1-0ubuntu3, 1.5.1-0ubuntu3.1), liblilv-0-0:amd64 (0.24.6-1, 0.24.6-1ubuntu0.1), google-chrome-stable:amd64 (83.0.4103.61-1, 83.0.4103.97-1), xserver-xorg-legacy:amd64 (2:1.20.8-2ubuntu2, 2:1.20.8-2ubuntu2.1), libnm0:amd64 (1.22.10-1ubuntu1, 1.22.10-1ubuntu2.1), network-manager:amd64 (1.22.10-1ubuntu1, 1.22.10-1ubuntu2.1), libgamemodeauto0:amd64 (1.5.1-0ubuntu3, 1.5.1-0ubuntu3.1), libapparmor1:amd64 (2.13.3-7ubuntu5, 2.13.3-7ubuntu5.1), gir1.2-gnomedesktop-3.0:amd64 (3.36.2-0ubuntu1, 3.36.2-0ubuntu2), xserver-xephyr:amd64 (2:1.20.8-2ubuntu2, 2:1.20.8-2ubuntu2.1), libgnome-desktop-3-19:amd64 (3.36.2-0ubuntu1, 3.36.2-0ubuntu2), xwayland:amd64 (2:1.20.8-2ubuntu2, 2:1.20.8-2ubuntu2.1), network-manager-config-connectivity-ubuntu:amd64 (1.22.10-1ubuntu1, 1.22.10-1ubuntu2.1), apparmor:amd64 (2.13.3-7ubuntu5, 2.13.3-7ubuntu5.1)
End-Date: 2020-06-07  11:23:39
```

---

### Post by JamButty on 2020-06-07
Ok, that was weird. After nearly 2 hours, the mouse suddenly came alive again. Cautiously marking this solved.

---

