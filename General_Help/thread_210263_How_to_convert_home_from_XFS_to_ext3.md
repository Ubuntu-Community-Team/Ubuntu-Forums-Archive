---
title: "How to convert /home from XFS to ext3?"
date: 2006-07-06
forum: General Help
---

### Post by tibbe on 2006-07-06
I just had some data loss when my computer, a IBM T41 laptop, completly froze on me. I guess that I had some data that were just stored in memory buffers. I don't know if this is XFS "fault" or not but I'm considering switching my /home partition to ext3 instead. Can I do this without first moving all my data (not much really) to another partition, reformatting and then moving it back? If not what's the best/safest way to switch filesystem?

---

### Post by reacocard on 2006-07-06
can't just convert. easiest way is like you said, copy to another partition, reformat, copy back. use the livecd to do it.

---

