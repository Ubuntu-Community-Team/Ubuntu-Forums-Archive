---
title: "Ubuntu freezes - out of memory?"
date: 2012-10-22
forum: General Help
---

### Post by M@s on 2012-10-22
This problem started appearing a while ago. I'm on 4 GB RAM, which I though would be enough, but I suspect not. Last time this happened I had Firerfox, rtorrent and Rhythmbox running while watching a 720p video on VLC. After a while I could see the memory meter reaching 94 %, then the movie sound started to lag and the mouse as well. It became worse and worse and in the end I had to do a hard reset. This happens a lot, especially if I use Ardour and other Jack applications.

I haven't experienced this before, and I don't know why suddenly everything seems to eat all this memory (I can't really point out a specific app causing this).

I suspect the lag is because my swap isn't working, it's always on 0% and the memory meter never reaches 100 % before it freezes... How can I tell? I've got a 5 GB swap partition dedicated for that.

I'm running Dreamstudio (Ubuntu 12.04, kernel 3.2.0-23 lowlatency).

---

### Post by dino99 on 2012-10-22
look at /etc/fstab , your swap partition entry should have these settings :

[HTML]UUID=  .......                      none   swap  sw                 0  0  [/HTML]

---

### Post by M@s on 2012-10-22
This is my swap entry:
```
/dev/mapper/cryptswap1        none    swap    sw                     0       0
```
But that's something else, isn't it? My swap partition is on /dev/sdc5. Was gonna try adding the correct line but I can't figure out how to find the UUID of the swap. blkid gives me nothing at all (it just keeps loading), and there is no entry for it in /dev/disk/by-uuid.

---

### Post by M@s on 2012-11-03
Fixed by reformatting the swap partition!

---

