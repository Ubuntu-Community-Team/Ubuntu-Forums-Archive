---
title: "Transmission bittorrent client - corrupt downloads"
date: 2008-03-04
forum: General Help
---

### Post by paradoxni on 2008-03-04
Is anyone else having corruption problems after using Tranmission (installed from synaptic)?

I downloaded several torrents consisting of multipart rars, which once downloaded to 100% with tranmission, I kept getting asked for a password when extracting the rar, copied to a windows machine where winrar reports CRC errors. I then opened the torrent again using bittornado which scans the files, downloads for a few secs then completes, the rar files then extract normally.

Anyone else seen this happen ?

---

### Post by isecore on 2008-03-31
Yeah, I have a similar problem.

Any torrent-downloads fail extraction or fail MD5 checks. In fact, any large downloads on my system will fail crc-checking. Iso-files will be corrupt, large zip/tar.gz archives will become corrupt as well.

First I thought this was due to broken memory. Odd as it might be, since my RAM is brand-new. Ran memtest for 12 hours while I slept. Not a single error.

Yet downloads are corrupt. When i sfv-check them using cksfv it discovers randomly corrupted files. Add to this that it's never the same files that are corrupt, it's always different files even if I haven't changed anything!

I'm running Hardy 64-bit, patched with everything latest.

---

### Post by paradoxni on 2008-04-01
I fixed my original problem, by installing a more up to date Transmission, but Im now trying out Hardy beta and the Transmission that comes preinstalled is working fine.

---

