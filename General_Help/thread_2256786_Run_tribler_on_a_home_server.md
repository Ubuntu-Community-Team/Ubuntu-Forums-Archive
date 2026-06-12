---
title: "Run tribler on a home server"
date: 2014-12-14
forum: General Help
---

### Post by michaelenda372 on 2014-12-14
I recently got an old dell desktop which I decided to turn into a media server so I set up a plex media server with ubuntu14.04. What the problem is is that I would like to also turn it into a seed box/ torrent downloader but I'm not sure how to run tribler without a desktop environment. I don't have to specifically run tribler if there is another anonymous torrent client that I could run from the command line.

---

### Post by ian-weisser on 2014-12-14
I'm not sure what you mean by an 'anonymous' torrent client.

The two big torrent clients for Linux, Deluge and Transmission, both have headless torrent daemons that can be controlled on the command line, web page, or GUI client, all on the same machine...or remotely.

For example:
To install the headless transmission daemon on the server: sudo apt-get install transmission-daemon
To install your control interface on your favorite system: sudo apt-get install transmission-remote-gtk
To install a backup command-line control interface on the server: sudo apt-get install transmission-cli

---

