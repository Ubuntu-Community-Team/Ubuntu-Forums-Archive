---
title: "Sync bittorrent clients on windows and ubuntu"
date: 2007-03-26
forum: General Help
---

### Post by djrobthaman on 2007-03-26
Hi there,

Just posting a quick, and hopefully easy, question.  Does anyone know how to sync bit torrent clients on both windows and ubuntu.  So that, for example, if I have torrents downloading using utorrent in windows (this actually is my ms client) that when I log in to ubuntu I can turn on another client and it will automatically pick up all my torrents, their positions and continue downloading from whichever point the windows client had reached and vice versa????

Thanks a lot,
Douglas

---

### Post by rich.bradshaw on 2007-03-26
If you used utorrent under wine in Ubuntu, you could possibly point your Windows utorrent at the same set of files and it may work...

Not sure how the format works, but I think that if you just copy the torrent and the partially downloaded file into the right place it would just carry on...

---

### Post by AlexKarm on 2007-03-26
I have been trying to set this up as well using Azureus.

I'm prety sure that clients manipulate partially downloaded files in very different ways, so you must keep the same client between OSes. That said, BitTornado, Azureus, and a bunch of others are platform independent.

As a last note, I suggest you learn from my mistakes in that Linux's NTFS support, even with the newest ntfs-3g driver, isn't absolutely perfect and Azureus uses rather low level commands while writing to disk (detailed cache management, etc). The end result was very corrupted torrents. I HIGHLY suggest that you save your torrents to a FAT32 partition that is shared between Linux and Windows, otherwise you end up with nothing productive.

Let us know if you get this working well, I would love to hear some more perspectives on it.

---

### Post by djrobthaman on 2007-03-26
Yep.. already got all my drives fat32 (except for ubuntu and windows partitions of course)... so the drive the downloads are being saved to are fat32.  Hopefully i'll figure some sort of automatic doohickey that can get this to work.  Will definitely post if I find it.

---

### Post by mattalexx on 2008-05-17
I know this thread is old but There is *nothing* on the Internet about it. Did anyone ever find a solution to this problem? I have a Ubuntu/Windows dual-boot with a FAT32 share.

Thank you.

---

