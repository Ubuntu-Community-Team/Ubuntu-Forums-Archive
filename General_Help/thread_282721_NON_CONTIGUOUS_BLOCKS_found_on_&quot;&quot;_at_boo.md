---
title: "NON CONTIGUOUS BLOCKS found on &quot;/&quot; at boot."
date: 2006-10-23
forum: General Help
---

### Post by ProjectGod on 2006-10-23
hi,

when my breezy badger starts after a few reboots it does an automatic <b>fsck</b>? of the / at boot up prior to mounting it? hmmm anyway when it did this previously no results would show up. but recently it came up with something along the lines of:

1.4% of files / blocks non-contiguous. 

or something. is this the windows equivalent of "fragmentation"? if so how do i "defrag" it so that blocks will be in future contiguous.

big thanks! :biggrin:

---

### Post by PriceChild on 2006-10-23
this is normal..... i hope ;)

---

### Post by Kateikyoushi on 2006-10-23
The check is scheduled for every 30th mount or so.
I wouldn't bother with it.

There is no online ext3 defragmentation tool. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first.

---

### Post by az on 2006-10-23
> **Kateikyoushi said:**
> The check is scheduled for every 30th mount or so.
I wouldn't bother with it.

There is no online ext3 defragmentation tool. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first.

Any ext3 filesystem can be mounted as ext2, you just don't use the journal.

But the point is that there is some fragmentation in all filesystems.  Ext2/ext3 filesystems are somewhat resistant to fragmentation.  The only exception is when the filesystem gets full.  When you approach something like 95 per cent full, you can expect more fragmentation.

If you free up some space, you can expect that fragmentation to go down over time, in my experience.


1.4 percent is pretty low - even on a partition that has been in use for five years, you will usually hover around five to seven percent.

---

### Post by ProjectGod on 2006-10-24
thanks for the replies :biggrin:
its a basic installation on a 20 gig partition. i have about 75% free space. i've used only 4 gig. and i can see no way of using more!

cheers

---

