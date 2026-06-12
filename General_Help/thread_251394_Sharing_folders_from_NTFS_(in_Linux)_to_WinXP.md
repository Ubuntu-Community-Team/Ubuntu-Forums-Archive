---
title: "Sharing folders from NTFS (in Linux) to WinXP"
date: 2006-09-05
forum: General Help
---

### Post by DageonYar on 2006-09-05
Hi all,

Recently made the jump to try Kubuntu, so I setup a dual boot on my XP machine. Kubuntu was smart enough to pick up on my NTFS partitions, and mount them properly under /media.

But I would like to share the NTFS partitions on my lan (read-only). I created a user, and an smbuser, and from the XP machine, I can login and see the home folder. I created a sym link (ln -s publix /media/hde1/myPublic/) in the smbuser's home folder, and can travers this sym link from the Linux machine (using the same user/smbuser account). But from the XP machine, the sym link doesn't even show up.

Any help?

---

### Post by PriceChild on 2006-09-05
You may instead want to try adding to /etc/samba/smb.conf following the examples in that file and sharing direct to the actual location of the mount.

Pricey

---

