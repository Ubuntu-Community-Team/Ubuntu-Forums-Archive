---
title: "Ktorrent locks up with certain torrent files"
date: 2007-10-17
forum: General Help
---

### Post by krazyman on 2007-10-17
Hi All,

I'm having a problem with Ktorrent when I try to open certain torrent files. Most of the time it's fine, but occasionally, a torrent file crops up that I can't seem to open. Ktorrent goes thru all the motions, asks me where to save, which particular files I want to dl, but then the processor goes into overdrive and Ktorrent stops responding. I can kill it, and then re-open, whereupon the torrent appears in the list, but it's not doing anything. If I try to delete the torrent from Ktorrent, Ktorrent then crashes and the K crash handling tool starts. The only way to remove the torrent is by deleting the ~/.kde/share/apps/ktorrent/tor0 dir. Then it's all fine again! But if I try the same torrent file we go through the hoop again.

I can post a link to a torrent file that does this if anyone's interested or can help?

Cheers.

---

### Post by gsiliceo on 2007-10-17
Arent those files, big files? like above 4 gigs big, if so, you cant download them to a fat32 partition nor fat, and im not sure about ntfs. Maybe is that just a guess.

---

### Post by krazyman on 2007-10-17
Nope, it's 238 MB. And the filesystem is ext3, with 16GB available...

---

### Post by krazyman on 2007-10-18
well here is a link to the torrent. It's an official bittorrent release so it's legally fine:

[http://www.isohunt.com/download/18722893/reggaeton]("http://www.isohunt.com/download/18722893/reggaeton")

I'd be interested if anyone else's ktorrent can't handle it!!!

---

### Post by krazyman on 2007-10-18
Has anyone else tried this torrent? I'd be really interested to know if it's just me...

---

### Post by gsiliceo on 2007-10-19
Is just you, i tried it and it didnt start downloading, but it didnt hang either. Have you tried reinstalling?

sudo aptitude purge ktorrent

sudo aptitude install ktorrent

---

### Post by krazyman on 2007-10-19
Thanks for your reply. I tried that and it didn't make any difference. I have had this problem on other machines too, so I can't help but think it's some persistent problem. Maybe it's something I'm doing, but it works flawlessly the rest of the time! Like I say, just certain torrents. Do you think it could be because of using gnome desktop rather than kde? Interesting that it doesn't download on yours either... Suggests there could really be a problem, just that mine likes it even less than yours???

---

### Post by krazyman on 2007-10-19
Right I've installed azureus and it works fine. So it's definitely a prob with ktorrent!!!

---

### Post by krazyman on 2007-10-20
After upgrading to Gutsy it's now working fine. Only thing is Kopete has given up now!!! ah well easy come easy go!

---

