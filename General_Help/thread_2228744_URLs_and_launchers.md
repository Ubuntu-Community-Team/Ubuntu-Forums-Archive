---
title: "URLs and launchers"
date: 2014-06-09
forum: General Help
---

### Post by runesvend on 2014-06-09
Does anyone know if it's possible to drag an URL from the browser onto a launcher, and have the launcher's application work with this URL?
I haven't been able to get it to work so far. Here's how my .desktop file looks:

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Name=TorrentPlay
Comment=Drop and BitTorrent magnet URI to start streaming a torrent
Exec=.torstream/torrentplay.py %u
NoDisplay=true
Icon=torstream
Terminal=false
StartupNotify=true
Type=Application
MimeType=x-scheme-handler/magnet;x-scheme-handler/http;
Categories=AudioVideo;Player;Video;
TargetEnvironment=Unity
X-Ayatana-Desktop-Shortcuts=IconInstall;
Name[en_US]=TorrentPlay

[IconInstall Shortcut Group]
Name=Install Icon
Exec=gksudo cp .torstream/torstream.png /usr/share/icons
TargetEnvironment=Unity

```

As far as I can tell, this should let me drag BitTorrent magnet URIs onto the launcher, or regular HTTP URLs. But it doesn't work. The launcher doesn't do anything when I drag it onto it, but dragging regular files works fine.

**EDIT:** I just found out this only applies to Google Chrome, with Firefox it works fine.

---

### Post by coffeecat on 2014-06-09
Post moved to own thread in General Help and title changed.

@runesvend, you posted to a thread in the Community Wiki Discussions sub-forum which is only for discussion about the content of wiki pages, not for technical support. Please see the Community Wiki Discussions sub-forum sticky:

[http://ubuntuforums.org/showthread.php?t=2074201](http://ubuntuforums.org/showthread.php?t=2074201)

---

