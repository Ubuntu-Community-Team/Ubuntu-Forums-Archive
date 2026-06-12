---
title: "Help backing up Ubuntu Server To FTP?"
date: 2013-02-03
forum: General Help
---

### Post by jingaling on 2013-02-03
Hi guys,

I've got a box that's running Ubuntu Server 12.04 for an OwnCloud instance. What I want to be able to accomplish is backup the OwnCloud data directory (for example /var/ocdata) to a remote host on my NAS drive.

I've heard that rsync is the way to go but from the research I've done it only supports SMB shares and they need to be mounted on the device being backed up. Is this correct?

Ideally what I would like it to do is compress the data into a .tar for example then transfer said data to my NAS drive via FTP. I's also like the compressed files to be named by the date of the backup and if possible automatically delete old backups once they hit a certain age (maybe 30 days).

Am I asking too much?

Thanks guys!

Kev

PS: My NAS does support SMB but I'd rather use FTP as I find it easier to use and more stable the SMB shares.

---

