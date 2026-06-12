---
title: "Rsync --delete question."
date: 2008-05-19
forum: General Help
---

### Post by Roasted on 2008-05-19
When you run an rsync command, such as

sudo rsync --delete /home/jason /media/backupdrive

It will delete any files that are not on the "host" drive from the "backupdrive." 

However, it deletes things FIRST.
Is there any way to make it delete things secondly?

Reason I ask, is say I have a 5 gig folder. I rename it. If I run my rsync script, it'll delete that 5 gig folder first. THEN it'll sync the newly named 5 gig folder from host to backupdrive. Now, it'd be just an extra nice security measure to have it delete secondly... because imagine that the once in a lifetime chance of my host drive dying DURING the 5 gig (very long) sync process?

See what I mean?

It's not a big deal. But I figured I'd ask.

---

### Post by vanadium on 2008-05-19
```

man delete

```

Better yet (or perhaps not, because deleting *afterwards* is a lot safer - you only need the extra drive space): just rename your 5 gig folder also on your backup, before doing the sync. Then, you will continue having a normal sync, where only the changes are propagated.

---

### Post by p_quarles on 2008-05-19
> **vanadium said:**
> ```

man delete

```

Better yet (or perhaps not, because deleting *afterwards* is a lot safer - you only need the extra drive space): just rename your 5 gig folder also on your backup, before doing the sync. Then, you will continue having a normal sync, where only the changes are propagated.
In order for that to work, I believe, you would need to manually manipulate the time stamp on the remote folder so that it matched the local one. I could be wrong, of course, but I think this might be more complicated than it looks at first glance.

---

### Post by Roasted on 2008-05-19
Yeah, I understand about drive space. I have 100 gig free on the backup drives I use, so that's not a concern. I was just simply curious if it were possible.

The only thing crucial I have to lose that I'd flip out over is pictures, but uh, I don't think I'll be renaming "Pictures" anything else anytime soon. And besides, that's why I do monthly backups of Pictures on DVD anyway!! :guitar:

---

### Post by vanadium on 2008-05-20
[quote=p_quarles]you would need to manually manipulate the time stamp on the remote folder so that it matched the local one.[/quote]

1) There is no need.
2) If there were a need, it would be easy to achieve.

---

