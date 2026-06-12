---
title: "Cannot open archive created by backup software"
date: 2008-07-06
forum: General Help
---

### Post by Robertjm on 2008-07-06
Hi all,

I'm having problems trying to backup my /home partition prior to doing a clean install of Ubuntu. Currently have Hardy Heron installed, with all the updates installed via Synaptic.

First time I used sbackup. It went overnight and created an archive that was about 30Gb in size. When I tried to open it up, it churned for a long time, but choked, indicating it was possibly corrupted. 

Next I installed QuickStart and tried using that. Again, I got an archive of 33Gb by the time it appeared finished. Just now, I tried opening the archive and received the following error:

gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

I am backing it up onto an Acomdata 500Gb external drive, connected by Firewire 400. The 100Gb partition I'm using is formatted as ext3, so I don't think there's a destination problem. However, since its bailed at apparently the same size I was wondering if there's some archive size limitation that I'm not aware of?

Thanks!!

Robert

---

