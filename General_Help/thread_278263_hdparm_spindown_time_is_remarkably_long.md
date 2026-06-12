---
title: "hdparm spindown_time is remarkably long"
date: 2006-10-16
forum: General Help
---

### Post by jazzgossen on 2006-10-16
I have a noisy HDD that I only want on during backups. Therefore I edited my /etc/hdparm.conf and set spindown_time to 1 for this disk (/dev/hda). I thought that would make the disk spin down after 5 seconds. It's not mounted at boot-up, so there should be nothing that accesses it and stops it from spinning down. Still, it takes several minutes before it spins down. Any ideas why?

---

