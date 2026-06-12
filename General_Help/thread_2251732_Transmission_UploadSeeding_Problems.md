---
title: "Transmission Upload/Seeding Problems"
date: 2014-11-06
forum: General Help
---

### Post by olias2 on 2014-11-06
[COLOR=#333333][FONT=Lucida Grande]hey[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]i have ubuntu servers,  transmission and 100MB/s upload/donwload on my local servers.
My problem is that transmission never goes above 20MB/s with average 10 MB/s uploadspeed per client with about 5MB/s max uploadspeed per torrent.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]For example if i seed with 1 server 1 torrent it has an upload speed about 3MB/s then if i start seeding some more the upload speed increases up to 10 MB/s but if it reaches this mark it doesn´t goes any further with add more torrent.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]When i`m seeding some data directly without transmission to another server i`m getting the 100MB/s.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Is there an option in the settings or something else which could increase the upload speed of the torrents/client?[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I have the deflaut transmission settings. [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Thx[/FONT][/COLOR]

---

### Post by ringstaart on 2014-11-06
Go to Edit > Preferences, and see if there are any speed limits enabled. If there are, disable them, or set them extremely high.

---

### Post by magamig on 2014-11-06
Try this:
Edit > Preferences > Uncheck all speed limits
Edit > Preferences > Donwloading > Maximium active downloads: 20
Edit > Preferences > Seeding > Uncheck all
Edit > Preferences > Network > 1. Port used: 51413, 2. Peer Limits > 1. maximimium peer per torrent 200, and peers overall to 1000

Change all this settings and say if it worked or not.

---

### Post by olias2 on 2014-11-06
i change the settings now i get an average upload about 25MB/s to 20MB/s.
it`s better but still not good enough.
{
    "alt-speed-down": 99999, 
    "alt-speed-enabled": false, 
    "alt-speed-time-begin": 540, 
    "alt-speed-time-day": 127, 
    "alt-speed-time-enabled": false, 
    "alt-speed-time-end": 1020, 
    "alt-speed-up": 50, 
    "bind-address-ipv4": "0.0.0.0", 
    "bind-address-ipv6": "::", 
    "blocklist-enabled": false, 
    "blocklist-url": "http://www.example.com/blocklist", 
    "cache-size-mb": 4, 
    "dht-enabled": true, 
    "download-dir": "/srv/downloads", 
    "download-limit": 99999, 
    "download-limit-enabled": false, 
    "download-queue-enabled": false, 
    "download-queue-size": 999999, 
    "encryption": 0, 
    "idle-seeding-limit": 9999999, 
    "idle-seeding-limit-enabled": false, 
    "incomplete-dir": "/srv/downloads-incomplete", 
    "incomplete-dir-enabled": false, 
    "lpd-enabled": true, 
    "max-peers-global": 99999, 
    "message-level": 2, 
    "peer-congestion-algorithm": "", 
    "peer-id-ttl-hours": 6, 
    "peer-limit-global": 34463, 
    "peer-limit-per-torrent": 20, 
    "peer-port": 51413, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": false, 
    "peer-socket-tos": "default", 
    "pex-enabled": true, 
    "port-forwarding-enabled": false, 
    "preallocation": 1, 
    "prefetch-enabled": true, 
    "queue-stalled-enabled": false, 
    "queue-stalled-minutes": 120, 
    "ratio-limit": 2, 
    "ratio-limit-enabled": false, 
    "rename-partial-files": true, 
    "rpc-authentication-required": false, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "{a4e68c4cce51c9035917495fef01b61f2b221e3bkmD8DDvh", 
    "rpc-port": 9091, 
    "rpc-url": "/transmission/", 
    "rpc-username": "transmission", 
    "rpc-whitelist": "127.0.0.1", 
    "rpc-whitelist-enabled": false, 
    "scrape-paused-torrents-enabled": true, 
    "script-torrent-done-enabled": false, 
    "script-torrent-done-filename": "", 
    "seed-queue-enabled": false, 
    "seed-queue-size": 999999,
    "speed-limit-down": 999999, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 99999, 
    "speed-limit-up-enabled": false, 
    "start-added-torrents": true, 
    "trash-original-torrent-files": false, 
    "umask": 18, 
    "upload-limit": 999999, 
    "upload-limit-enabled": false, 
    "upload-slots-per-torrent": 9999, 
    "utp-enabled": true, 
    "watch-dir": "/srv/watchfoldertorrents", 
    "watch-dir-enabled": true
}

---

