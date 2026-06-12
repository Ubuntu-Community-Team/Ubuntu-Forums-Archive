---
title: "'Empty trash' doesn't delete from all drives"
date: 2007-10-28
forum: General Help
---

### Post by hamster_billy on 2007-10-28
I've noticed that when I empty the trashcan it only empties the trash stored on my Ubuntu ext3 partition and my FAT32 usb stick if it happens to be connected. However, any .Trash folders on NTFS drives or partitions aren't emptied. Is this standard behaviour? Files in these don't show up in the trashcan in Nautilus. Is there a way to make the trashcan register that they exist? It's no major problem now that I can manually delete them, just a bit annoying, though before I realised that 6 Gb of my 20 Gb NTFS partition was hiding in the trash I was pretty worried.

---

### Post by Virgofenix on 2007-10-28
Yeah. That's normal. Idk the reason particularly, but I believe it has something to do with the drive permissions. For that matter, you can't mount NTFS drives as /home. 

It really is inconvenient. I wanted to have a large partition where I could dump all my data and have it shared between Windows and Linux.

---

### Post by hamster_billy on 2007-10-28
That's what I was doing too (a 'large' partition being only 20 Gb on my laptop!). I guess I'll just live with the inconvenience.

---

