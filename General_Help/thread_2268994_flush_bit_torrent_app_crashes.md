---
title: "flush bit torrent app crashes"
date: 2015-03-12
forum: General Help
---

### Post by William_Klee on 2015-03-12
Flush crashes every time I try to set a separate folder to move finished downloads to. Anyone else having this problem? Any suggestions on solving it?

I thought about directly editing ~/.flush/client.conf, hoping there'd be something there I could change, but there's nothing in there about moving finished download. There is this line, near the bottom:

```
  download_to = "/home/william/Downloads/bit-torrent/downloading";


```

so if the syntax follows, it's be something like:

```
move_complete_download_to = "/home/william/Downloads/bit-torrent/finished";


```

Anyone know what the actual entry would be?

system specs:
Dell Inspiron 13 7347
CPU: 3.0GHz i7
RAM: 8 GB
HD: 930 GB Mushkin SSD
OS: Ubuntu / Kubuntu / Lubuntu 14.10

---

