---
title: "rTorrent no Upload"
date: 2007-02-19
forum: General Help
---

### Post by michio on 2007-02-19
I installed rTorrent and torrents download perfectly but I never get any upload. The speed is always at 0. I assume the ports were forwarded correctly because I can download. I attempted to use the bind function and setting it to my i.p address but that returns a ```
rtorrent: Could not open/bind a port for listening: Cannot assign requested address
```

my .rtorrent.rc looks like this
```
# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 130

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 17

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 590
#upload_rate = 60

# Default directory to save the downloaded torrents.
directory = /download

# Default session directory.
#session = /home/xxxx/torrents/sessions

# Watch a directory for new torrents, and stop those that have been deleted.
#schedule = watch_directory,5,5,load_start=/home/homedir/torrents/torrentfiles/*.torrent
#schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,stop_on_ratio=200,200M,2000

# Port range to use for listening.
port_range = 61407-61607

# Start opening ports at a random position within the port range.
port_random = yes

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

check_hash = yes
```

thanks!

---

### Post by konsole on 2007-02-19
> **michio said:**
> I installed rTorrent and torrents download perfectly but I never get any upload. The speed is always at 0. I assume the ports were forwarded correctly because I can download. I attempted to use the bind function and setting it to my i.p address but that returns a 

Your ports aren't forwarded correctly or aren't open. Do an external test ( [https://www.grc.com/x/portprobe=61407](https://www.grc.com/x/portprobe=61407) )

---

### Post by michio on 2007-02-19
The ports are forwarded on my router to this my computers IP, when i run the grc probe the ports come up as 'stealth' is there any setting in ubuntu that could be blocking these ports, since i know the ports are forwarded.

---

### Post by konsole on 2007-02-19
iptables can block ports on your linux box but I think your problem is that the ports are not open on your router. Check your router docos to do this.

BTW, you don't need 200 open ports for bittorrent, just use one open tcp port on your router and forward that to your linux box.

In your .rtorrent.rc use:
port_range = 61407-61407

---

### Post by michio on 2007-02-20
if the ports aren't open why can I download files with no trouble?
The ports are forwarded fine unless my router suddenly stopped working... I have been using ddwrt on my router for years and it has always run just fine.

---

### Post by konsole on 2007-02-20
u need to understand a bit about how tcp/ip and firewalls work else you wouldn't have asked that question. Good luck.

[http://www.cisco.com/univercd/cc/td/doc/cisintwk/ito_doc/ip.htm](http://www.cisco.com/univercd/cc/td/doc/cisintwk/ito_doc/ip.htm)

[http://en.wikipedia.org/wiki/Stateful_Packet_Inspection#Description](http://en.wikipedia.org/wiki/Stateful_Packet_Inspection#Description)

---

