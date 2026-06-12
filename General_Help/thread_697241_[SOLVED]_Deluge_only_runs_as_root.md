---
title: "[SOLVED] Deluge only runs as root?"
date: 2008-02-14
forum: General Help
---

### Post by ric0689 on 2008-02-14
I have just installed Deluge from synaptic with no problems, but when I open it from the applications menu it shows up on the title bar for 10 seconds and disappears. When I run it from the terminal I get this
```
ric@ric-desktop:~$ deluge
checking for ubuntu...
found and fixing ubuntu
ric@ric-desktop:~$ checking for ubuntu...
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin WebSeed
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin Scheduler
Initialising plugin MoveTorrent
Initialising plugin NetworkGraph
Initialising plugin FlexRSS
Initialising plugin TorrentNotification
Initialising plugin WebUi
Initialising plugin BlocklistImport
Initialising plugin DesiredRatio
Initialising plugin TorrentFiles
Initialising plugin SpeedLimiter
Initialising plugin TorrentCreator
Initialising plugin Search
Initialising plugin NetworkHealth
Applying preferences
Starting DHT...
No DHT file to resume
terminate called after throwing an instance of 'asio::system_error'
  what():  Permission denied
```

but when I do
```

sudo deluge
```
 
it runs just fine.

any suggestions? or should I just run it as root?

---

### Post by pointone on 2008-02-14
Try deleting the Deluge configuration folder in your home directory, ~/config/.deluge or ~/.deluge; can't remember which. Make sure to move torrents (if any) from this folder first (if you want to keep them).

---

### Post by ric0689 on 2008-02-14
Thanks worked like a charm!

---

