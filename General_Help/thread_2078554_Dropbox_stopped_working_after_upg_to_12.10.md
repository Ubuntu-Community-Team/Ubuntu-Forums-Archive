---
title: "Dropbox stopped working after upg to 12.10"
date: 2012-10-31
forum: General Help
---

### Post by matej on 2012-10-31
I got problems with Dropbox after upgrade to 12.10. Dropbox is telling "Can't access Dropbox folder" in the status and is not syncing. 

I tried Ubuntu Dropbox package and deb package directly from dropbox.com.  Both have the same problem. I also tried to delete .dropbox folder and sync Dropbox folder from scratch.  

Help is really appreciated, this bug paralyzes my workflow a lot.

---

### Post by COMECON on 2013-01-20
bump
I have the same problem and the same error... Anybody knows a solution?

esy

---

### Post by ld114 on 2013-01-20
I don't know if this will help, but I have thought that dropbox has some sort of interaction with grub files (for example I deleted a partition with another distro, and dropbox had to be re-connected afterwards).

Maybe try "removing completely" dropbox with synaptic, rebooting, running sudo update-grub, and then re-installing dropbox with the deb from the dropbox website. However, I have stayed with 12.04 for the moment, so I have no evidence that this would work.

---

### Post by matej on 2013-01-23
Try to turn off desktop indexing and reboot, see here: [https://forums.dropbox.com/topic.php?id=95441#post-522158](https://forums.dropbox.com/topic.php?id=95441#post-522158)

---

