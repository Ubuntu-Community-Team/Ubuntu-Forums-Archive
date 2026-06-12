---
title: "restart the computer makes mpd delete the database."
date: 2008-03-06
forum: General Help
---

### Post by El_Belgicano on 2008-03-06
MPD:
Everytime I restart my comp, I have to recreate the db, the status file is ok since when the db is recreated it start playing where I left it without doing anything else.

My ~/.mpdconf:
```
port			"6600"
music_directory         "/media/win2/musique/"
playlist_directory      "~/.mpd/playlists"
db_file                 "~/.mpd/mpddb"
log_file                "~/.mpd/mpd.log"
error_file              "~/.mpd/mpd.error"
state_file         "~/.mpd/state"
```

Thanks.

---

### Post by firmit on 2008-05-06
MPD is not crazy about ~/ - try writing the full path.

---

### Post by El_Belgicano on 2008-05-07
Ok, I've made the changes and shutdown the computer this morning, I'll see the result asa I get back from the university... Thanx

---

### Post by El_Belgicano on 2008-05-08
:( didn't work like expected...

---

### Post by El_Belgicano on 2008-05-23
still no one for that issue?

---

### Post by vanadium on 2008-05-23
Perhaps it is a fault in the way mpd is installed? In the command used to start mpd? It is certainly not normal behaviour. I have my music on a removable drive, and mpd just works correctly, with or without the drive connected at boot time.

---

