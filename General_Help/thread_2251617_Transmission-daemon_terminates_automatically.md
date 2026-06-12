---
title: "Transmission-daemon terminates automatically"
date: 2014-11-05
forum: General Help
---

### Post by chaminga2 on 2014-11-05
[COLOR=#000000][FONT=Arial]I have a VPS running on Ubuntu 14.04.1 LTS. In that, i have installed transmission daemon to use as seedbox.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I can connect to it remotely and download torrents. But it works only for few minutes. Remote connection get hangs automatically.Then i have to run /etc/init.d/transmission-daemon restart to make it work again. This keeps happening.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]How to solve this ?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Here is transmission daemon config.
[/FONT][/COLOR]
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
    "blocklist-enabled": false, 
    "blocklist-url": "http://www.example.com/blocklist", 
    "cache-size-mb": 4, 
    "dht-enabled": true, 
    "download-dir": "/var/www/torrents", 
    "download-limit": 100, 
    "download-limit-enabled": 0, 
    "download-queue-enabled": true, 
    "download-queue-size": 5, 
    "encryption": 1, 
    "idle-seeding-limit": 30, 
    "idle-seeding-limit-enabled": false, 
    "incomplete-dir": "/home/debian-transmission/Downloads", 
    "incomplete-dir-enabled": false, 
    "lpd-enabled": false, 
    "max-peers-global": 200, 
    "message-level": 2, 
    "peer-congestion-algorithm": "", 
    "peer-id-ttl-hours": 6, 
    "peer-limit-global": 200, 
    "peer-limit-per-torrent": 50, 
    "peer-port": 51413, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": false, 
    "peer-socket-tos": "default", 
    "pex-enabled": true, 
    "port-forwarding-enabled": false, 
    "preallocation": 1, 
    "prefetch-enabled": 1, 
    "queue-stalled-enabled": true, 
    "queue-stalled-minutes": 30, 
    "ratio-limit": 2, 
    "ratio-limit-enabled": false, 
    "rename-partial-files": true, 
    "rpc-authentication-required": true, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "XXXXX", 
    "rpc-port": 9091, 
    "rpc-url": "/transmission/", 
    "rpc-username": "admin", 
    "rpc-whitelist": "*", 
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

### Post by CaptainMark on 2014-11-05
Run it with the -e flag or --logfile flag and use it to specify a location to log to for the duration of that instance, you can then start rummaging through the logs for anything useful.

---

### Post by papibe on 2014-11-05
Hi  chaminga2. Welcome to the forum ):P

A few ideas:

Check the logs for error messages:
```
grep transmission /var/log/syslog
```
Since transmission-daemon runs as special user (debian-transmission), make sure that the download directory belongs to that user:
```
sudo chown debian-transmission\: /var/www/torrents
```
Also that directory needs to have special permissions so make sure you have them:
```
sudo chmod 4775 /var/www/torrents
```
Downloads usually sum up over time, and eat disk space. Make sure the download partition is NOT in the root partition, or at least you have enough space (both space and inodes).

Last thought:
Most decent VPS providers allow torrent downloads nowadays. However, you may need to make sure you follow their terms of service in terms of bandwidth, caps, hours, etc.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by chaminga2 on 2014-11-06
> **CaptainMark said:**
> Run it with the -e flag or --logfile flag and use it to specify a location to log to for the duration of that instance, you can then start rummaging through the logs for anything useful.

Thanks for the replay. I restarted daemon and ran transmission-daemon -f --logfile /var/log/transmission.log

Here what i got.

```
[2014-11-06 08:18:20.648 EST] Transmission 2.84 (14307) started (session.c:736)
[2014-11-06 08:18:20.648 EST] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:824)
[2014-11-06 08:18:20.648 EST] RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
[2014-11-06 08:18:20.648 EST] RPC Server Whitelist enabled (rpc-server.c:1037)
[2014-11-06 08:18:20.648 EST] Couldn't bind port 51413 on 0.0.0.0: Address already in use (Is another copy of Transmission already running?) (net.c:371)
[2014-11-06 08:18:20.648 EST] Couldn't bind port 51413 on ::: Address already in use (Is another copy of Transmission already running?) (net.c:371)
[2014-11-06 08:18:20.648 EST] UDP Couldn't bind IPv4 socket (tr-udp.c:263)
[2014-11-06 08:18:20.648 EST] DHT Generating new id (tr-dht.c:310)
[2014-11-06 08:18:20.648 EST] Using settings from "/root/.config/transmission-daemon" (daemon.c:557)
[2014-11-06 08:18:20.648 EST] Saved "/root/.config/transmission-daemon/settings.json" (variant.c:1214)
[2014-11-06 08:18:28.649 EST] Port Forwarding State changed from "Not forwarded" to "???" (port-forwarding.c:92)
[2014-11-06 08:20:52.813 EST] Transmission 2.84 (14307) started (session.c:736)
[2014-11-06 08:20:52.813 EST] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:824)
[2014-11-06 08:20:52.813 EST] RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
[2014-11-06 08:20:52.813 EST] RPC Server Whitelist enabled (rpc-server.c:1037)
[2014-11-06 08:20:52.813 EST] Couldn't bind port 51413 on 0.0.0.0: Address already in use (Is another copy of Transmission already running?) (net.c:371)
[2014-11-06 08:20:52.813 EST] Couldn't bind port 51413 on ::: Address already in use (Is another copy of Transmission already running?) (net.c:371)
[2014-11-06 08:20:52.813 EST] UDP Couldn't bind IPv4 socket (tr-udp.c:263)
[2014-11-06 08:20:52.813 EST] DHT Generating new id (tr-dht.c:310)
[2014-11-06 08:20:52.813 EST] Using settings from "/root/.config/transmission-daemon" (daemon.c:557)
[2014-11-06 08:20:52.813 EST] Saved "/root/.config/transmission-daemon/settings.json" (variant.c:1214)
[2014-11-06 08:21:00.814 EST] Port Forwarding State changed from "Not forwarded" to "???" (port-forwarding.c:92)
[2014-11-06 08:22:12.146 EST] Saved "/root/.config/transmission-daemon/settings.json" (variant.c:1214)
[2014-11-06 08:22:12.146 EST] DHT Not saving nodes, DHT not ready (tr-dht.c:358)
[2014-11-06 08:22:12.146 EST] Port Forwarding Stopped (port-forwarding.c:180)

```
What can be the issue ?

---

### Post by chaminga2 on 2014-11-06
> **papibe said:**
> Hi  chaminga2. Welcome to the forum ):P

A few ideas:

Check the logs for error messages:
```
grep transmission /var/log/syslog
```
Since transmission-daemon runs as special user (debian-transmission), make sure that the download directory belongs to that user:
```
sudo chown debian-transmission\: /var/www/torrents
```
Also that directory needs to have special permissions so make sure you have them:
```
sudo chmod 4775 /var/www/torrents
```
Downloads usually sum up over time, and eat disk space. Make sure the download partition is NOT in the root partition, or at least you have enough space (both space and inodes).

Last thought:
Most decent VPS providers allow torrent downloads nowadays. However, you may need to make sure you follow their terms of service in terms of bandwidth, caps, hours, etc.

Hope it helps. Let us know how it goes.
Regards.

Thanks [COLOR=#000000]papibe. Here is the output for [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]grep transmission /var/log/syslog.[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR]```
Nov  6 05:23:22 vps transmission-daemon[28882]: Transmission 2.84 (14307) started (session.c:736)Nov  6 05:23:22 vps transmission-daemon[28882]: RPC Server Adding address to whitelist: * (rpc-server.c:824)
Nov  6 05:23:22 vps transmission-daemon[28882]: RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
Nov  6 05:23:22 vps transmission-daemon[28882]: RPC Server Whitelist enabled (rpc-server.c:1037)
Nov  6 05:23:22 vps transmission-daemon[28882]: RPC Server Password required (rpc-server.c:1040)
Nov  6 05:23:22 vps transmission-daemon[28882]: Couldn't bind port 51413 on 0.0.0.0: Address already in use (Is another copy of Transmission already running?) (net.c:371)
Nov  6 05:23:22 vps transmission-daemon[28882]: Couldn't bind port 51413 on ::: Address already in use (Is another copy of Transmission already running?) (net.c:371)
Nov  6 05:23:22 vps transmission-daemon[28882]: Port Forwarding Stopped (port-forwarding.c:180)
Nov  6 05:23:22 vps transmission-daemon[28882]: UDP Couldn't bind IPv4 socket (tr-udp.c:263)
Nov  6 05:23:22 vps transmission-daemon[28882]: DHT Generating new id (tr-dht.c:310)
Nov  6 05:23:22 vps transmission-daemon[28882]: Using settings from "/var/lib/transmission-daemon/info" (daemon.c:557)
Nov  6 05:23:22 vps transmission-daemon[28882]: Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
Nov  6 05:23:22 vps transmission-daemon[28882]: transmission-daemon requiring authentication (daemon.c:577)
Nov  6 05:23:22 vps transmission-daemon[28882]: Loaded 1 torrents (session.c:1992)
Nov  6 05:23:26 vps transmission-daemon[28882]: Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
Nov  6 05:23:26 vps transmission-daemon[28882]: DHT Not saving nodes, DHT not ready (tr-dht.c:358)
Nov  6 05:23:26 vps transmission-daemon[28882]: Port Forwarding Stopped (port-forwarding.c:180)
Nov  6 05:23:26 vps transmission-daemon[28882]: Closing session
Nov  6 05:27:55 vps transmission-daemon[28968]: Transmission 2.84 (14307) started (session.c:736)
Nov  6 05:27:55 vps transmission-daemon[28968]: RPC Server Adding address to whitelist: * (rpc-server.c:824)
Nov  6 05:27:55 vps transmission-daemon[28968]: RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
Nov  6 05:27:55 vps transmission-daemon[28968]: RPC Server Whitelist enabled (rpc-server.c:1037)
Nov  6 05:27:55 vps transmission-daemon[28968]: RPC Server Password required (rpc-server.c:1040)
Nov  6 05:27:55 vps transmission-daemon[28968]: Couldn't bind port 51413 on 0.0.0.0: Address already in use (Is another copy of Transmission already running?) (net.c:371)
Nov  6 05:27:55 vps transmission-daemon[28968]: Couldn't bind port 51413 on ::: Address already in use (Is another copy of Transmission already running?) (net.c:371)
Nov  6 05:27:55 vps transmission-daemon[28968]: Port Forwarding Stopped (port-forwarding.c:180)
Nov  6 05:27:55 vps transmission-daemon[28968]: UDP Couldn't bind IPv4 socket (tr-udp.c:263)
Nov  6 05:27:55 vps transmission-daemon[28968]: DHT Generating new id (tr-dht.c:310)
Nov  6 05:27:55 vps transmission-daemon[28968]: Using settings from "/var/lib/transmission-daemon/info" (daemon.c:557)
Nov  6 05:27:55 vps transmission-daemon[28968]: Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
Nov  6 05:27:55 vps transmission-daemon[28968]: transmission-daemon requiring authentication (daemon.c:577)
Nov  6 05:27:55 vps transmission-daemon[28968]: Loaded 2 torrents (session.c:1992)
Nov  6 05:28:00 vps transmission-daemon[28968]: Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
Nov  6 05:28:00 vps transmission-daemon[28968]: DHT Not saving nodes, DHT not ready (tr-dht.c:358)
Nov  6 05:28:00 vps transmission-daemon[28968]: Port Forwarding Stopped (port-forwarding.c:180)
Nov  6 05:28:00 vps transmission-daemon[28968]: Arrow.S03E04.480p.HDTV.x264-mSD Removing torrent (torrent.c:1916)
Nov  6 05:28:00 vps transmission-daemon[28968]: Arrow.S03E04.480p.HDTV.x264-mSD Pausing (torrent.c:1857)
Nov  6 05:28:00 vps transmission-daemon[28968]: Saved "/var/lib/transmission-daemon/info/resume/Arrow.S03E04.480p.HDTV.x264-mSD.4716547682f843fc.resume" (variant.c:1214)
Nov  6 05:28:00 vps transmission-daemon[28968]: Closing session
Nov  6 08:09:34 vps transmission-daemon[29495]: Transmission 2.84 (14307) started (session.c:736)
Nov  6 08:09:34 vps transmission-daemon[29495]: RPC Server Adding address to whitelist: * (rpc-server.c:824)
Nov  6 08:09:34 vps transmission-daemon[29495]: RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
Nov  6 08:09:34 vps transmission-daemon[29495]: RPC Server Whitelist enabled (rpc-server.c:1037)
Nov  6 08:09:34 vps transmission-daemon[29495]: RPC Server Password required (rpc-server.c:1040)
Nov  6 08:09:34 vps transmission-daemon[29495]: Port Forwarding Stopped (port-forwarding.c:180)
Nov  6 08:09:34 vps transmission-daemon[29495]: UDP Failed to set receive buffer: requested 4194304, got 266240 (tr-udp.c:78)
Nov  6 08:09:34 vps transmission-daemon[29495]: UDP Please add the line "net.core.rmem_max = 4194304" to /etc/sysctl.conf (tr-udp.c:83)
Nov  6 08:09:34 vps transmission-daemon[29495]: UDP Failed to set send buffer: requested 1048576, got 266240 (tr-udp.c:89)
Nov  6 08:09:34 vps transmission-daemon[29495]: UDP Please add the line "net.core.wmem_max = 1048576" to /etc/sysctl.conf (tr-udp.c:94)
Nov  6 08:09:34 vps transmission-daemon[29495]: DHT Generating new id (tr-dht.c:310)
Nov  6 08:09:34 vps transmission-daemon[29495]: Using settings from "/var/lib/transmission-daemon/info" (daemon.c:557)
Nov  6 08:09:34 vps transmission-daemon[29495]: Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
Nov  6 08:09:34 vps transmission-daemon[29495]: transmission-daemon requiring authentication (daemon.c:577)
Nov  6 08:09:34 vps transmission-daemon[29495]: Loaded 3 torrents (session.c:1992)
Nov  6 08:10:18 vps transmission-daemon[29495]: DHT Attempting bootstrap from dht.transmissionbt.com (tr-dht.c:248)
Nov  6 08:18:06 vps transmission-daemon[29567]: Transmission 2.84 (14307) started (session.c:736)
Nov  6 08:18:06 vps transmission-daemon[29567]: RPC Server Adding address to whitelist: * (rpc-server.c:824)
Nov  6 08:18:06 vps transmission-daemon[29567]: RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
Nov  6 08:18:06 vps transmission-daemon[29567]: RPC Server Whitelist enabled (rpc-server.c:1037)
Nov  6 08:18:06 vps transmission-daemon[29567]: RPC Server Password required (rpc-server.c:1040)
Nov  6 08:18:06 vps transmission-daemon[29567]: Port Forwarding Stopped (port-forwarding.c:180)
Nov  6 08:18:06 vps transmission-daemon[29567]: UDP Failed to set receive buffer: requested 4194304, got 266240 (tr-udp.c:78)
Nov  6 08:18:06 vps transmission-daemon[29567]: UDP Please add the line "net.core.rmem_max = 4194304" to /etc/sysctl.conf (tr-udp.c:83)
Nov  6 08:18:06 vps transmission-daemon[29567]: UDP Failed to set send buffer: requested 1048576, got 266240 (tr-udp.c:89)
Nov  6 08:18:06 vps transmission-daemon[29567]: UDP Please add the line "net.core.wmem_max = 1048576" to /etc/sysctl.conf (tr-udp.c:94)
Nov  6 08:18:06 vps transmission-daemon[29567]: DHT Generating new id (tr-dht.c:310)
Nov  6 08:18:06 vps transmission-daemon[29567]: Using settings from "/var/lib/transmission-daemon/info" (daemon.c:557)
Nov  6 08:18:06 vps transmission-daemon[29567]: Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
Nov  6 08:18:06 vps transmission-daemon[29567]: transmission-daemon requiring authentication (daemon.c:577)
Nov  6 08:18:06 vps transmission-daemon[29567]: Loaded 3 torrents (session.c:1992)
Nov  6 08:18:43 vps transmission-daemon[29567]: DHT Attempting bootstrap from dht.transmissionbt.com (tr-dht.c:248)
Nov  6 08:18:49 vps transmission-daemon[29567]: Arrow.S03E04.480p.HDTV.x264-mSD State changed from "Incomplete" to "Complete" (torrent.c:2161)
Nov  6 08:19:04 vps transmission-daemon[29567]: Arrow.S03E03.480p.HDTV.x264-mSD State changed from "Incomplete" to "Complete" (torrent.c:2161)



```

---

### Post by papibe on 2014-11-06
It looks like there are two instances of transmission running.

Could you post the results of this:
```
ps aux | grep transmission
```
Regards.

---

### Post by chaminga2 on 2014-11-07
> **papibe said:**
> It looks like there are two instances of transmission running.

Could you post the results of this:
```
ps aux | grep transmission
```
Regards.

Here is the output.


```
debian-+  1541  0.2  3.0  69312  7904 ?        Tsl  09:20   0:00 /usr/bin/transmission-daemon -f --config-dir /var/lib/transmission-daemon/info
root      1587  0.0  0.2   2556   684 pts/2    S+   09:23   0:00 grep --color=auto transmission



```

Thanks again for the support.

---

### Post by papibe on 2014-11-07
Thanks. It seems that not the case.

It may be this case: [Transmission uTP and UDP buffer optimizations]("http://falkhusemann.de/blog/2012/07/transmission-utp-and-udp-buffer-optimizations/").

Where the systems defaults are too small for a VPS on the 'real Internet'. I would either disable utp, or increase the system parameters as suggested on the link.

Let us know if that makes a difference.
Regards.

PS: to disable utp, remember to stop transmission, make the change on the file, and start transmission again.

---

### Post by chaminga2 on 2014-11-08
> **papibe said:**
> Thanks. It seems that not the case.

It may be this case: [Transmission uTP and UDP buffer optimizations]("http://falkhusemann.de/blog/2012/07/transmission-utp-and-udp-buffer-optimizations/").

Where the systems defaults are too small for a VPS on the 'real Internet'. I would either disable utp, or increase the system parameters as suggested on the link.

Let us know if that makes a difference.
Regards.

PS: to disable utp, remember to stop transmission, make the change on the file, and start transmission again.

I already added [COLOR=#000000][FONT=Ubuntu Mono]net.core.rmem_max = 4194304[/FONT][/COLOR] and [COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]net.core.wmem_max = 1048576[/FONT][/COLOR] to [COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/etc/sysctl.con.[/FONT][/COLOR] When i [COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]```
[COLOR=#000000][FONT=Consolas]sysctl -p[/FONT][/COLOR]
``` as you mentioned in that link follow error displayed.


```
root@vps:~# sysctl -p
sysctl: permission denied on key 'net.core.rmem_max'
sysctl: permission denied on key 'net.core.wmem_max'

```

---

### Post by papibe on 2014-11-08
What are the current values of those parameters?

Could you post the result of this:
```
sysctl net.core.rmem_max net.core.wmem_max
```
Regards.

EDIT: the error 'sysctl: permission denied on key 'net.core.rmem_max'' usually is display when a non root user tries to run sysctl. Apparently you are running as root, but what happens when you run:
```
sudo sysctl -p
```

---

### Post by chaminga2 on 2014-11-08
> **papibe said:**
> What are the current values of those parameters?

Could you post the result of this:
```
sysctl net.core.rmem_max net.core.wmem_max
```
Regards.

EDIT: the error 'sysctl: permission denied on key 'net.core.rmem_max'' usually is display when a non root user tries to run sysctl. Apparently you are running as root, but what happens when you run:
```
sudo sysctl -p
```



```
root@vps:~# sysctl net.core.rmem_max net.core.wmem_max
net.core.rmem_max = 133120
net.core.wmem_max = 133120

```

I already logged as root user.


```
root@vps:~# sudo sysctl -p
sysctl: permission denied on key 'net.core.rmem_max'
sysctl: permission denied on key 'net.core.wmem_max'

```



```
-rw-r--r-- 1 root root                 2139 Sep  3 14:02 sysctl.conf
```

---

### Post by papibe on 2014-11-08
I see.

My guess is that this is a VPS running on top of something like OpenVZ, or other 'container' technology, so you can't change kernel parameters because they are shared between several virtual machines.

I would suggest disabling the utp protocol, and see how that goes against stability.
Regards.

---

