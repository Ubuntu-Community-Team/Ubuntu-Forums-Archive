---
title: "A fast way of making a cp"
date: 2022-09-29
forum: General Help
---

### Post by klapvogn on 2022-09-29
Hey,

Me again ):P

Is there a fast way to ```
cp -al
``` men it should be done from a mergerfs mount, to a local harddrive?

```
cp: cannot create hard link  Invalid cross-device link
```

---

### Post by HermanAB on 2022-09-29
A hard link (another name for a file) only works on a single file system.

---

### Post by The Cog on 2022-09-29
Whats more, you only have one copy - editing either filename edits your one-and-only copy. That could be awkward if you edit one, hoping to leave the other as a backup or change record.

-s, --symbolic-link might be better than making hard links - it's easier to tell there's only one copy, and works across different filesystems. I think that's the answer to the original question.

---

### Post by klapvogn on 2022-09-30
> **The Cog said:**
> Whats more, you only have one copy - editing either filename edits your one-and-only copy. That could be awkward if you edit one, hoping to leave the other as a backup or change record.

-s, --symbolic-link might be better than making hard links - it's easier to tell there's only one copy, and works across different filesystems. I think that's the answer to the original question.

Hey,

thanks and how would I archive this?

---

### Post by The Cog on 2022-10-01
If you want to make an archive than you will have to copy the data, not just link to it. **cp -a** is good for that. Make sure you use the command **sync** when you've finished, and don't unplug the archive until the sync command finishes, whihc will be when the disk cache in memory has been flushed to disk.

---

### Post by klapvogn on 2022-10-01
Thanks :)

---

