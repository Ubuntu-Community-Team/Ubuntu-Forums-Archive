---
title: "rTorrent, Watch folders failure"
date: 2014-02-12
forum: General Help
---

### Post by robin8 on 2014-02-12
Hello,

I've set-up rTorrent on my VPS, manually added downloads are downloading correctly, but when i'm downloading via an torrent watch folder, the download stops randomly.
This is my watch folder config:

```
# Watch a directory for new torrentsschedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=
schedule = watch_directory,10,10,"load_start=/home/robin/rtorrent/watches/all/*.torrent"
schedule = watch_directory_2,10,10,"load_start=/home/robin/rtorrent/watches/movies/*.torrent, d.set_custom1=movies, d.set_directory=/home/robin/rtorrent/downloads/movies"
schedule = watch_directory_3,10,10,"load_start=/home/robin/rtorrent/watches/series/*.torrent, d.set_custom1=series, d.set_directory=/home/robin/rtorrent/downloads/series"
```

Any idea whats wrong?

Thanks!

---

### Post by robin8 on 2014-02-12
```
schedule = tied_directory,10,10,start_tied=schedule = untied_directory,10,10,close_untied=
```

Hmm, commented this, and it's working.

---

