---
title: "Attempt to repair FAT32 - total failure"
date: 2008-05-23
forum: General Help
---

### Post by HyperHacker on 2008-05-23
I had an SD card with a corrupted FAT32 filesystem, and tried to repair it using fsck.vfat. It would report some errors, then abort with a message like "Read 32 bytes at 1024278528:Input/output error" and not actually do anything to the card.
So I used Windows XP's repair tool, and it (as usual) discarded the directory structure and just put all recovered files in FOUND.000 with incrementing numbers as names. Not something I want to pick through on Windows, but I figure since Thunar (or the file command if need be) does a good job of identifying file types based on content, it'd be easier in Xubuntu.
When I mount the card in Xubuntu, it shows nothing at all in FOUND.000, not even hidden files. :confused: Why does Windows see them and Xubuntu not?

---

### Post by Steve413z on 2008-05-23
did you try reformatting it?

---

### Post by HyperHacker on 2008-05-23
That's what I ended up doing (copying the recovered files from Windows and formatting), the idea was to recover without formatting though. Xubuntu wouldn't even touch the card, so I had to do that in Windows too.

Curiously, Windows *did* recover the files (though without names, and many were corrupt), but also copied in a bunch of files from the hard disk. O_o

---

