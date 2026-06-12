---
title: "Tracker creates 32 GB file-meta.db"
date: 2008-01-30
forum: General Help
---

### Post by sfgreenwood on 2008-01-30
I have Gutsy 64-bit installed on a Fujitsu-Siemens Amilo 1600 laptop with an AMD Mobile Athlon processor. I've been using it to encode CDs to FLAC on a USB external drive. I started having problems with logging in this evening, and after much fiddling, found that the root partition was full. I managed to create enough space to start a session, and when I ran Disk Usage Analyzer, I found that ~/.cache/tracker was taking 99% of the available disk space. Examining further, I found that file-meta.db was 32Gb in size and file-index.db was 4Gb in size.

I don't use tracker so I have stopped it as suggested elsewhere, but I can't see how the default config can allow databases to get so big. In fact, I can't even see how to configure it. Is this a bug?

---

### Post by articpenguin on 2008-01-30
do you have a lot of files? i only have 500 photos on my harddisk and my meta.db is 100MB.

---

### Post by sfgreenwood on 2008-01-31
My music collection is currently about 150 CDs, so if you say an average of 10 tracks per CD, and an average size of around 25Mb per track that's ~1500 tracks in about 50Gb. This is all that I have been using this machine for. I installed KDE4 from an unofficial repository and have been keeping the OS updated but otherwise that's it.

If the idea of tracker is to keep track of changes to file systems then I can see why a metafile would grow. What I don't understand is why there isn't a limit on its size by default.

---

