---
title: "Very fast rtorrent question - reseed"
date: 2008-01-04
forum: General Help
---

### Post by krelkor on 2008-01-04
I have a ton of large files that ive already downloaded in utorrent and ktorrent and i would like to be able to redownload the torrents from my private trackers and point them towards my already completed data

i know ktorrent(import existing download) and utorrent allows this, does rtorrent?

thanks!

---

### Post by mali2297 on 2008-01-04
If you put the downloaded files in the assigned download directory and the corresponding torrent files in the watch directory, then rTorrent should be able to make the connection.

I have the downloaded files in ~/Downloads and the torrent files in ~/watch, so my ~/.rtorrent.rc includes these lines:
```

# Default directory to save the downloaded torrents.
directory = ./Downloads

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=./watch/*.torrent
schedule = untied_directory,5,5,stop_untied=

```

---

