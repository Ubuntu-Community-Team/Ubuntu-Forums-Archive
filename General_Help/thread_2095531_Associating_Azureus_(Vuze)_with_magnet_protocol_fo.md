---
title: "Associating Azureus (Vuze) with magnet protocol for Chrome"
date: 2012-12-17
forum: General Help
---

### Post by dzchimp on 2012-12-17
What is the correct method to associate Magnet links in Chrome with Azureus, in KDE? I've tried in vain to try creating a .desktop file in /usr/share/services with the name azureus.desktop, then tried running:

```
xdg-mime default azureus.desktop x-scheme-handler/magnet
```

Also tried with /usr/share/applications/azureus.desktop: 

```
[Desktop Entry]
Categories=Java;Network;FileTransfer;P2P;
Comment=Download and share files using the BitTorrent P2P network
Exec=/usr/bin/vuze %U
GenericName=BitTorrent client
Icon=Azureus
MimeType=application/x-bittorrent;x-scheme-handler/magnet;
Name=Vuze
Type=Application

```

Nothing seems to work. I've also read that I could create a .protocol file to do this. However I couldnt understand how to.

How can I get magnet torrent links to properly open up in Vuze? Ktorrent opens them by default fine. However I cant find a new .protocol file created, or a .desktop file with the correct info for ktorrent.

OS: Debain Squeeze (However this problem seems to be a KDE thing and could be found in Archlinux/Ubuntu/SUSE forums)

I've found that Firefox handles magnet links internally, however Chrome/Chromium leaves it to the OS and hence we've got to configure it ourselves.

---

### Post by dzchimp on 2012-12-19
Forgive me for bumping up this topic.

---

