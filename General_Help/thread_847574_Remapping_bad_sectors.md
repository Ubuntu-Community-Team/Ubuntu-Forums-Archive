---
title: "Remapping bad sectors"
date: 2008-07-02
forum: General Help
---

### Post by Richard_ on 2008-07-02
Is it possible to automatically remap bad sectors when they are encountered? Or even better, to format the drive with, say, ext3 and scan for bad sectors and mark them as inacessible?

Now, to throw a spanner in the works; is it possible to do this when I have 2 hard drives set up in software RAID 1, and only one of the drives has a few bad sectors? The drive isn't failing, and has had the same bad sectors for a few years already.

I've tried to zero the drive a few times already, but it still has the same bad sectors. I'm not particularly worried about data loss, and my wanting to use RAID is just for convenience sake.

Any suggestions?

Thanks :-)

---

### Post by brian_p on 2008-07-02
> **Richard_ said:**
> Is it possible to automatically remap bad sectors when they are encountered? Or even better, to format the drive with, say, ext3 and scan for bad sectors and mark them as inacessible?

```
man e2fsck
```

The -c option.

```
man badblocks
```

[/QUOTE]

---

