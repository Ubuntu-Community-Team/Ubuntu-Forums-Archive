---
title: "Deluge doesn't auto-open Torrent files"
date: 2007-12-24
forum: General Help
---

### Post by Just Pete on 2007-12-24
I'm using Deluge 0.5.7.95 on Ubuntu 7.10, and I use TED (Torrent Episode Downloader) to find many torrents.

TED normally passes the torrent files to Deluge for opening, but recently Deluge hasn't been opening the files. Specifically, I can open the torrents from Deluge using File -> Add Torrent and selecting the torrent file, but I cannot doubleclick the torrent file itself (which normally launches in my default Bittorrent program - currently Deluge), or right-click the file and Open using Deluge. Both of the failing options open a window in the task bar (That I can't expand to view) which sticks around for 30 seconds or so then closes, accomplishing nothing.

I've tried launching the torrent file in a terminal using '/usr/sbin/deluge <torrent>', which lauches Deluge but does not load the torrent file, and gives no errors in the terminal window.

I've deleted the persistant.state file, and also prefs.state - neither of which had any effect.

I've enabled the Event Logging plugins with all plugins - I get nothing.

Anything else I can do?

---

### Post by Just Pete on 2007-12-27
No response here, but figured I'd help anyone browsing for answers.

This has been fixed in development, and will be in the next 'final' release of deluge. Note that neither the final version nor the current latest release is in the standard Ubuntu repositories.

See the thread on the deluge forums  [here]("http://forum.deluge-torrent.org/viewtopic.php?f=7&t=961&p=4606#p4606")

---

### Post by FuturePilot on 2007-12-31
I'm using Deluge 0.5.8 and it still doesn't open .torrent files when I double click them. Actually Deluge doesn't even start when I double click on a .torrent file. :(

---

### Post by Chibi-Tatsu on 2008-01-01
Likewise here.  I can, as the OP mentioned, add a torrent through Deluge, but I cannot add by opening with in swiftweasel or by double-click.  Currently using .5.8-1

---

