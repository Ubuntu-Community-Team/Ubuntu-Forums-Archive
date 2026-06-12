---
title: "I need help with rsync syntax."
date: 2007-09-16
forum: General Help
---

### Post by MetalMusicAddict on 2007-09-16
I need to back up the content of folder **A** to folder **B**. I want it to only copy whats new from **A** to **B**.

I was thinking my command would look like:
```
rsync -varu --inplace /media/A/ /media/B
```

Look correct?

---

### Post by por100pre1 on 2007-09-16
```
rsync -r -t -v --progress --delete /media/A/ /media/B/
```

This one also deletes whatever is in B that is no longer in A and shows progress.

Hope this helps. :)

EDIT: (Be careful before trying it, I'm a n00b!)

EDIT: If B is not a backup (A and B should be synchronized), I think your setup will do the trick...

---

### Post by MetalMusicAddict on 2007-09-16
Awesome. The **--delete** was something I needed. :)

```
rsync -aru --inplace --delete /media/A/ /media/B
```

Thanx for the tip. I'm using this for a cron job.

---

