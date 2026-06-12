---
title: "file -s reports &quot;(needs journal recovery)&quot;"
date: 2007-07-30
forum: General Help
---

### Post by murraymca on 2007-07-30
Hi,

I just noticed that file -s reports:
/dev/hda1: Linux rev 1.0 ext3 filesystem data (needs journal recovery)

This is my root partition.  I've had a bit of a search around but not much luck - I don't know anything about file systems, just wondering if anyone knew if this was as bad as it sounds, or if it can safely be ignored?

I booted from a live cd and fsck reported that the file system was clean.

Apologies if this is a stupid question ;)

Thanks for any help.

---

### Post by ddrichardson on 2007-07-30
Don't worry about it. When ext3 is mounted and the journal is active, it sets a flag that says the journal needs recovery and that the feature flag is incompatible. 

It stops an unclean ext3 filesystem being mounted as ext2 and losing the journal recovery.

Once the journal has been recovered, that clears the flag and you can mount it as ext2. So in other eords it should clear once recovered.

---

### Post by murraymca on 2007-07-30
Thanks for the quick reply.  I started reading about what you said before bed, but like I said I'm completely new to file systems so it was a bit over my head.

Thanks again for the quick reply :)

---

