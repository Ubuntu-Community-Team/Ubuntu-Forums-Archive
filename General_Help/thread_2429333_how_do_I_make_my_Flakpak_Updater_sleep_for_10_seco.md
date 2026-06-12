---
title: "how do I make my Flakpak Updater sleep for 10 seconds during startup?"
date: 2019-10-17
forum: General Help
---

### Post by ardouronerous on 2019-10-17
```
[Desktop Entry]
Version=1.1
Type=Application
Name=Flatpak Updater
Comment=Show and install available flatpak updates
Icon=system-software-update
Exec=lxterminal -e bash -c 'flatpak update && read -p "Press any key to continue"'
Actions=
Categories=System;Settings;
```

I've created this Flatpak Updater, because in Lubuntu, I do not get notifications for updates for flatpaks, I always have to check for updates myself.

I put the executable in *[FONT=courier new]/?HOME/.config/autostart[/FONT]*, but there's an issue with my WIFI, it takes 5 to 10 seconds for my WIFI to establish a connection, so my executable fails to check for flatpak updates, so I want it to start 10 seconds after startup, thanks.

Thanks.

---

### Post by Holger_Gehrke on 2019-10-17
You could try changing the exec-line to
```
Exec=lxterminal -e bash -c '**sleep 10s ;** flatpak update && read -p "Press any key to continue"'
```
(change in bold)

Holger

---

### Post by ardouronerous on 2019-10-17
That worked, thanks.

---

### Post by ardouronerous on 2019-10-17
[ATTACH=CONFIG]284196[/ATTACH]

Is it possible to give a title to the script like Flatpak Updater instead of bash as seen in the picture? Thanks.

---

### Post by ardouronerous on 2019-10-18
Figured it out:
```
lxterminal -t "Flatpak Updater" -e bash -c 'sleep 10s ; flatpak update && read -p "Press any key to continue"'
```

---

