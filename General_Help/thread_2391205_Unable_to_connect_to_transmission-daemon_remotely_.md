---
title: "Unable to connect to transmission-daemon remotely since upgrade"
date: 2018-05-07
forum: General Help
---

### Post by changeableface on 2018-05-07
Hi, 

I have a server running headlessly that serves has two purposes, 1.) Back up files for long-term storage 2.) Run transmission-daemon. 

This server is running Ubuntu 16.04.4 LTS, and transmission-daemon 2.84. 

This server has been running without issue for almost two years, but recently I upgraded to this latest version transmission-daemon 2.84 from 2.82 (from memory). Since then I've been unable to connect to it using Transmission GUI or via web browser as I would normally. 

I've validated that no change has taken place to my settings.json file, but have added this as well as it's location to this message for review. I'd be grateful if anyone is able to point out my issue. 

/home/matthew/.config/transmission-daemon/settings.json

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
    "download-dir": "/media/files/downloads",
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 1,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/media/files/temp",
    "incomplete-dir-enabled": true,
    "lpd-enabled": false,
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
    "port-forwarding-enabled": true,
    "preallocation": 1,
    "prefetch-enabled": 1,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "rename-partial-files": true,
    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-host-whitelist": "0.0.0.0",
    "rpc-host-whitelist-enabled": false,
    "rpc-password": "{7f3ea18d657fd006b724942658495d5953ffc9a9D//8B8ze",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "matthew",
    "rpc-whitelist": "127.0.0.1,*.*.*.*",
    "rpc-whitelist-enabled": false,
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
    "upload-slots-per-torrent": 14,
    "utp-enabled": true
}

```

I've checked ufw and the port remains open, but when visiting the URL I'm met with a 403 message;

```

[COLOR=#000000][FONT=Times]Unauthorized IP Address.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]Either disable the IP address whitelist or add your address to it.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.[/FONT][/COLOR]

```

I've tried adding *.*.*.* to the whitelist and then enabling it, but that did me no favors. Some people have mentioned that the correct location for settings.json is /var/lib/transmission-daemon/info/settings.json however, if I stop the service, make changes to this file then start the service again it never encrypts the password as it does with the file located at /home/matthew/.config/transmission-daemon/settings.json

If anyone has any ideas or needs more info, please let me know. 

Thanks, 
- Matt

---

### Post by nlee2 on 2018-05-07
Could try rollback to 2.82 on 16.04 or upgrade to 18.04 and run 2.92 (working for me)

---

### Post by changeableface on 2018-05-08
I'd considered updating, but as the LTS version of 18.04.1 hasn't come out yet I'd rather wait - also this works for plenty of other people so why not me? Downgrading is only a partial solution as I'll be locked to that version until some unknown time.

---

### Post by ea-mail-wc on 2018-05-10
Have a look at

transmission-daemon.conf

in

/etc/init

this determines where transmission-daemon looks for it's configuration files.

Change the lines for setuid and setgid to

setuid matthew
setgid matthew

You'll probably have to edit as SU.

Restart the transmission-daemon.

Transmission should then pick up your configuration file from [COLOR=#000000]/home/matthew/.config/transmission-daemon/[/COLOR]

---

### Post by nlee2 on 2018-05-10
Unable to reproduce. I did a fresh install of ubuntu server 16.04. Did a update and installed transmission-daemon. Copied the contents of your config without any change into /etc/transmission-daemon/settings.json. I am able to access transmission-daemon from another subnet by name and ip. Double checked settings in the webgui to ensure that they matched your config.

The fact that your install is picking up config from /home indicates a departure from standard install of transmission-daemon on ubuntu 16.04.

---

### Post by changeableface on 2018-05-16
@ea-mail-wc - Thanks for the suggestion, i've just tried this to no avail. [IMG]https://i.imgur.com/vPBv5YM.png[/IMG]

---

### Post by changeableface on 2018-05-16
@nlee2 thanks for testing, perhaps I need to nuke this server from space and start again. It's a sledgehammer approach but it'll likely solve the problem

---

