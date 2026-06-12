---
title: "apt-get problem"
date: 2008-01-06
forum: General Help
---

### Post by omni814 on 2008-01-06
apt-get keeps asking me for the Gutsy Install CD and I don't have it, and I'd rather not download it again and burn another copy. Also, I'd like to not have to carry it everywhere with me, in the off chance I try to install something which needs the install CD.

Is there any way to make it search online for a package instead of looking on the install CD?  I've looked through the man page and cannot find an option for this, and I must not have the right search terms in google.`:-P  Thanks

---

### Post by taurus on 2008-01-06
System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and remove the check mark for CDROM.  Close that window and press Refresh.

Make sure you have a check mark for other repos except the last one, Source code.

---

### Post by omni814 on 2008-01-06
Thank you very much, that did it :)

---

