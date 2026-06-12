---
title: "Transmission daemon slowly crawls to download"
date: 2016-12-12
forum: General Help
---

### Post by timonoj on 2016-12-12
Hi guys!

This is a bit of a weird situation. Up until now I had transmission daemon running from a NAS. But it hogs the CPU a bit much and every month I get a random reboot on the NAS. Since I built a specific Ubuntu Server for additional functions (on a core i5 NUC), I'm using that one now to download torrents. Here's the thing: The one on the NAS manages to get way more seeders/leechers and downloads way faster than the one on the new server, for exactly the same torrent. Same upload/download/sharing/encryption settings as far as I can tell. My router has UPNP enabled so it should automatically negotiate the ports (it does on the NAS one). Biggest difference I can see, the NAS transmission is the ancient v2.84 and the one on the Ubuntu server is v2.92. But the NAS is the faster one.

Help?

EDIT: Adding the settings.json:
```

{
    "alt-speed-down": 50,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 50,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": true,
    "blocklist-url": "http://www.bluetack.co.uk/config/level1.gz",
    "cache-size-mb": 4,
    "dht-enabled": true,
    "download-dir": "/media/NASdownload/Torrents",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 2,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/media/NASdownload/transmission/incomplete",
    "incomplete-dir-enabled": false,
    "lpd-enabled": true,
    "max-peers-global": 200,
    "message-level": 1,
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 200,
    "peer-limit-per-torrent": 250,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
 "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": false,
    "preallocation": 1,
    "prefetch-enabled": true,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "rename-partial-files": true,
    "rpc-authentication-required": true,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-password": "[]",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "my_local_user",
   "rpc-whitelist": "192.168.*.*",
    "rpc-whitelist-enabled": true,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "speed-limit-down": 100,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 100,
    "speed-limit-up-enabled": false,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 18,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": true
}
```

---

