---
title: "Wrong name of mounted folders on desktop"
date: 2019-04-21
forum: General Help
---

### Post by schwinni on 2019-04-21
Hello all together,

I am running Ubuntu 18.10 and there is a weird behavior when mounting folders.
I have mounted a NTFS partition to /mnt/data.
When I mount a folder "/mnt/data/Backup" to "/home/schwinni/Backup" via ```
mount --bind /mnt/data/Backup  /home/schwinni/Backup
``` the link on the desktop has the name "Data".
When I mount a second folder "test", the link is also called "Data".
Normally the names should be "Backup" and "test".

That problem also exist when I mount the folder via /etc/fstab.

What could cause that problem?

Thanks in advance!

Best regards
Chris

---

