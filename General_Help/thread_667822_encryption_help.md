---
title: "encryption help"
date: 2008-01-14
forum: General Help
---

### Post by Ocxic on 2008-01-14
I just re-installed my system, and I'm using encryption, I have a storage partition that i can no longer mount, I'm asked for my Luks password, and it says it opened successfully but when i try to mount the drive I get an error about bad block size and such, I'm running xfs_repair right now, it's searching for a secondary super block. I don't want to loose anything please help.

I made sure not to erase anything on that partition it should still work

---

### Post by Washer on 2008-01-14
Good luck. I've *always* been hosed when my devices start talking about super blocks. Started using truecrypt ~1 year ago & i'm never going back.

---

### Post by HermanAB on 2008-01-14
Ooops - XFS???  You should only use Ext3 with encrypted volumes.  Now you know why...

My sincere condolences with the death of all your data...

Herman

---

### Post by Ocxic on 2008-01-15
I discovered the problem when I re-installed it re-initalized the encrypted partition. hosed everything. damn. no re-installs allowed anymore i guess.

---

