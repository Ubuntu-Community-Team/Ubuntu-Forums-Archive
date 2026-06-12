---
title: "Sonata, MPD, and Playlists"
date: 2008-04-20
forum: General Help
---

### Post by ntowakbh on 2008-04-20
I have Sonata, and MPD installed, and configured, but now, my only problem that remains is that, while I can see my playlists, I can't listen to them.  Any help as to figuring out what is wrong?  I've spent awhile Googling around, but my searches all turned up nothing.  Anyone have a clue?

Any help would be greatly appreciated.

---

### Post by newb1e on 2008-04-20
what happens when you click a song in the playlist?

---

### Post by ntowakbh on 2008-04-20
No individual songs comp up, just the playlist name, and telling it "add" does nothing.

---

### Post by newb1e on 2008-04-20
I think you need to create a link to your music folder first
```
sudo ln -s /your/music/folder /usr/share/mpd/music
```
then create database for mpd
```
mpd --create-db
```

Maybe you need to restart too, I'm not sure.

---

### Post by ntowakbh on 2008-04-20
```
cannot setgid for user "mpd" at line 35: Operation not permitted
``` 
Comes up when I try to create the database.

---

### Post by newb1e on 2008-04-21
my bad, you need sudo to do that
```
sudo mpd --create-db
```

---

