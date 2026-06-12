---
title: "rTorrent delete torrent &amp; files when seeding complete"
date: 2015-11-23
forum: General Help
---

### Post by kjetil-asphoug on 2015-11-23
Hi. I've been trying all sorts of event keys and cant get rTorrent to delete the torrent and its files when the seeding has reached its goal.

Does anyone have the knowledge to help me with this?

Basically i want it to do this: 
1. Download
2. Complete download
3. Run filebot on download complete
4. Seed until 1,5 ratio.
5. Delete torrent and files when ratio goal reached.


My rtorrent.rc: 

scgi_port = localhost:5000
port_range = 11360-11360
download_rate = 8192
upload_rate = 1024
min_peers = 100
max_peers = 300
min_peers_seed = 100
max_peers_seed = 300
max_uploads = 10
max_downloads_global = 2
max_uploads_global = 10
directory = /home/server/Downloads/rTorrent
session = /home/server/.rtorrent.session
ratio.enable=
ratio.min.set=150
port_random = no
peer_exchange = no
system.method.set_key=event.download.finished,filebot_amc,"execute={/var/www/html/rutorrent/rtorrent-postprocess,$d.get_base_path=,$d.get_name=,$d.get_custom1=}"
system.method.set = group.seeding.ratio.command, d.close=

---

