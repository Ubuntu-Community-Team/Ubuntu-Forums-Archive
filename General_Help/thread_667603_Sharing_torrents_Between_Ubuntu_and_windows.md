---
title: "Sharing torrents Between Ubuntu and windows"
date: 2008-01-14
forum: General Help
---

### Post by Spaz O Mataz on 2008-01-14
As the title says is it possible to share downloading torrents between Ubuntu and windows. The reason being i am dual booting as I cannot get fl studios to run propperly under wine. and I always have a torrent program open but how do you get windows and ubuntu to share the downloads, any programs available for both that can understand each others data. thanks in advance

---

### Post by miceagol on 2008-01-14
Just tell the torrent program in Ubuntu to save to a folder on the NTFS disk...

---

### Post by djrobthaman on 2008-01-14
I believe that this can be done by setting up either 1 or 2 folders for torrents (depending on which programs you use).  Let's assume you use deluge in linux and utorrent in windows.  Up until the last time I used utorrent you couldn't automatically save torrents in the same folder that it automatically loaded from.

So set up 2 torrent folders, "windows save" and "windows load", and 1 download folder, "global download".  Have utorrent set up so it automatically saves all torrent files to "windows save", automatically loads all torrents in "windows load" and automatically saves the downloaded files to "global download".

In linux, have deluge set up to automatically load torrent files from "windows save" and automatically save to "windows load" and, again, automatically save all downloaded files to "global download".

The one thing is, and I'm not sure if this can be automated, you need to make sure to delete all the torrents that you're finished with.  Otherwise, if you were to stop seeding the file and move it somewhere else on your hd, the download would restart because it would load the torrent again.

---

