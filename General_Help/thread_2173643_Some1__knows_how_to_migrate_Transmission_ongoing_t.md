---
title: "Some1  knows how to migrate Transmission ongoing torrents to another OS installation?"
date: 2013-09-10
forum: General Help
---

### Post by hurinth on 2013-09-10
Hi, I have 2 partitions with 2 Ubuntu distros. One of them has Transmission with about 4 ongoing torrents. I want to migrate them to the new Ubuntu install on my other partition without loosing each torrent progress. The download directory where the torrents are storing the .part files is a third partition commong to both Ubuntu installs. I have tried right clicking the torrent > Copy magnet link to clipboard, then invoking Transmission on the other install, but it starts from scratch, even though I point it to the same download folder.

Any ideas?

THanks in advance.

---

### Post by hurinth on 2013-09-10
Ok so, without the torrents at hand (because I checked the "Move .torrent file to the trash" option initially), the way I was able to migrate the torrents was, to right click on the source torrent > Copy magnet link to clipboard, paste it on a document, reboot the machine into the new Ubuntu install, open Transmission > Open URL then past the magnet link.

Transmission will start fetching metadata and then it will show its progress as 0%, you would think (I did) it started from scratch, but if you right click on the torrent again, click on Verify local data, then it will show the actual progress based on the files already downloaded.

---

