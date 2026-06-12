---
title: "Bulk edit of torrent location"
date: 2014-10-29
forum: General Help
---

### Post by zweiundzwei on 2014-10-29
With recent versions of Ubuntu, the file system location of removable hard drives has change from /media/HARDDRIVE to /media/user/HARDDRIVE. I use my external hard drive to store torrents. Therefore I need to update all their locations. I can't do it via the Transmission GUI because most of the torrents are in seperate folders. I had to do this before and I remember using a script (?) from this forum that essentially edited the content every .torrent file in the Transmission config folder and did a search replace for the torrent location string.  I cannot find it anymore for the life of me, but I also really don't want to do this by hand. Any help would be appreciated.

---

### Post by zweiundzwei on 2014-10-29
This is what I was looking for: [transmission-batch-move]("https://github.com/vlevit/transmission-batch-move/blob/master/transmission-batch-move")

---

