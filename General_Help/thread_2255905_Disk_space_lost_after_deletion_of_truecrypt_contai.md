---
title: "Disk space lost after deletion of truecrypt container"
date: 2014-12-08
forum: General Help
---

### Post by djpemberton on 2014-12-08
I just deleted (shift-del) a truecrypt container on an external hd. After the deletion, I noticed that the space wasn't freed. Is there something that I can do to free that space again?

---

### Post by kpatz on 2014-12-08
Is/was the container still mounted?  Linux doesn't free up the space when unlinking a file until the file is no longer in use.

What filesystem are you using on the external drive?

---

### Post by djpemberton on 2014-12-08
No. It wasn't mounted. It has a ntfs filesystem. I never changed that.

---

