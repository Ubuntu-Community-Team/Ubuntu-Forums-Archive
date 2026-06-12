---
title: "Tixati Ubuntu 12.04 Magnet Links issue on Chrome/Chromium"
date: 2013-11-25
forum: General Help
---

### Post by alisamar on 2013-11-25
[COLOR=#000000][FONT=Verdana]When I click the magnet link on Chrome/Chromium tixati running but nothing else happens. Load Transfer screen should normally show up to start downloading. It seems Tixati not getting the meta-info.[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
settings are as follows:

[/FONT][/COLOR]```
[COLOR=#000000][FONT=Verdana]$ xdg-mime default tixati.desktop application/x-bittorrent x-scheme-handler/magnet [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][Desktop Entry] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Version=1.0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Encoding=UTF-8 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Name=Tixati [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]GenericName=BitTorrent Client [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Comment=Share files over BitTorrent [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Exec=tixati %F [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Icon=tixati [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Terminal=false [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Type=Application [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]MimeType=application/x-bittorrent;x-scheme-handler/magnet; [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Categories=Internet;Network;FileTransfer;P2P;GTK; [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]X-Desktop-File-Install-Version=0.15[/FONT][/COLOR]
```[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by mehdus on 2014-09-01
Hi,

I just figured out how to get it working, following [http://portland.freedesktop.org/xdg-utils-1.0/xdg-desktop-menu.html](http://portland.freedesktop.org/xdg-utils-1.0/xdg-desktop-menu.html)

> If the application is able to open URLs in addition to local files then %u or %U can be used instead of %f or %F.

Magnet links worked for me after I replaced "%F" in the "Exec" line with "%U".

---

