---
title: "Program running in background but not showing in taskbar"
date: 2014-03-08
forum: General Help
---

### Post by leopheard on 2014-03-08
Hi all,

I have an issue with a cryptocurrency wallet program (Peercoin) running automatically at startup but not actually showing in the taskbar. I autorun it via the file ppcoin.desktop in /home/username/.config/autostart which is as follows:

[Desktop Entry]
Type=Application
Name=PPCoin
Exec=/opt/PPcoin030/bin/32/ppcoin-qt -min
Terminal=false
Hidden=false

The only way I can get the program to come up is to use sudo killall ppcoin-qt and then run it again from the above folder. Then the icon appears in the system tray and I can use the program.

Any ideas? Any help would be very much appreciated.

---

