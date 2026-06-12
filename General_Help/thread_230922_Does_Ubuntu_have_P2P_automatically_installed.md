---
title: "Does Ubuntu have P2P automatically installed?"
date: 2006-08-06
forum: General Help
---

### Post by leo_m on 2006-08-06
Does Ubuntu, in its zeal for everything anti-closed source and to promote free sharing, install P2P programs by default and are these activated by default?

I saw bit-torrent installed and an attempt to uninstall it says Ubuntu desktop will be uninstalled as well!!

I then desired to configure it myself and installed bittorrent-gui, but I could not find any entry created in any of the menus.

If there is P2P installed and enabled by default in Ubuntu, I want to disable that in my private setup, because I do not like the idea of my machine being used for uploads/downloads or for P2P without my explicit permission.

---

### Post by fene on 2006-08-06
as long as your not explicitely share some folders with the p2p community, nobody will download stuff from your machine. there's no need to uninstall bit-torrent.

in a "raw" ubuntu installation, almost all tcp and udp ports are closed and your machine is not run the risk of abuse.

---

### Post by orb9220 on 2006-08-06
The program has to be run first before you or others can share.

Just like you can't play and listen to music till you run the program to  play music.

It is an application installed not a service running at startup.

---

### Post by bionnaki on 2006-08-06
there is a bittorrent service that is shown to be shutting down upon rebooting, but that service is not active at all. keep in mind that bittorrent doesnt necessarily mean p2p-illegal downloading. 

you can remove this service completely if it bothers you that much (even though it is not doing anything at all): sudo update-rc.d bittorrent remove

see: [http://www.ubuntuforums.org/showthread.php?t=209078&highlight=bittorrent+shutdown](http://www.ubuntuforums.org/showthread.php?t=209078&highlight=bittorrent+shutdown)

and you can safely remove ubuntu-desktop. no ill affect on your machine other than hindering a dist-upgrade (at which time you can reinstall ubuntu-desktop)

---

### Post by 3rdalbum on 2006-08-07
leo_m, all the above posters are correct. To further put your mind at ease, though, BitTorrent only shares data when you open a .torrent file in it.

So your computer is safe.

---

