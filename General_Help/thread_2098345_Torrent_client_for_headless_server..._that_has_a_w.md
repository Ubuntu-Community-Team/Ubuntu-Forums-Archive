---
title: "Torrent client for headless server... that has a web interface?"
date: 2012-12-26
forum: General Help
---

### Post by Roasted on 2012-12-26
I'm on the hunt for a torrent client that has a web interface that I can use on my 12.04.1 Ubuntu Server install. I've heard that rtorrent has some third party web front ends, but I'm trying to hold off on venturing down that path just yet in case there's something else I'm missing that's more of an all in one ready to go install it - bam done type of package.

I've traditionally used Transmission, so naturally I began to look towards Transmission's CLI package, but I'm not really digging up much. Most people are just saying "I just run transmission file.torrent" or whatever via SSH and that's that. That's all well and good but I'd much rather have a web interface to manage them. Is there anything I'm missing?

---

### Post by mcduck on 2012-12-26
Transmission has plenty of Web-based UI's available, so you don't need to go for SSH/CLI approach if you don't want to:

[http://www.transmissionbt.com/resources/]("http://www.transmissionbt.com/resources/")

...and of course Deluge has a Web UI as well.

---

### Post by Cheesemill on 2012-12-26
+1 for Transmission or Deluge, they both have WebUI's.

---

### Post by Roasted on 2012-12-26
Pardon my ignorance, but last I installed Transmission, I had to open Transmission and enable the web interface.

How can I do such a thing on a headless, CLI only server?

---

### Post by mcduck on 2012-12-26
try starting the daemon first:

```
transmission-daemon
```
...as far as I know, that should already enable the Web UI. If not, there's probably a config file you can edit to enable it.

---

### Post by iMac71 on 2012-12-26
Perhaps this topic might help you:
[https://forum.transmissionbt.com/viewtopic.php?f=8&t=12555](https://forum.transmissionbt.com/viewtopic.php?f=8&t=12555)

---

### Post by Roasted on 2012-12-26
> **mcduck said:**
> try starting the daemon first:

```
transmission-daemon
```
...as far as I know, that should already enable the Web UI. If not, there's probably a config file you can edit to enable it.

Good call. It seems as if you need to install transmission-daemon, as it's not part of transmission-cli (at least, that's how it was for me on 12.04). Once done I ran transmission-daemon and it launched. I was able to hit myip:9091 and I logged in using transmission/transmission as the default credentials. Very nice! Now I just need to do a little digging to edit the user so instead of transmission/transmission it's roasted/mysupersecretpassword. :D

EDIT - I also noticed that I would get a permission denied error when the torrents would try to save, which confused me because the directory was root:transmission @ 775 perms. I set it to 777 and let one begin to download then ran ls -l on it. It turns out debian-transmission is the actual name of the user who's saving the torrents. As a result, I added debian-transmission to be the group with 775 perms and all ran well.

The only thing I really have to do yet is change the password/user account on the actual transmission setup, however since I'm not forwarding transmission out externally from my LAN I'm not sure it's a huge deal.

---

