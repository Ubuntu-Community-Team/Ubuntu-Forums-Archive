---
title: "Quick question regarding NTFS on ubuntu"
date: 2007-10-19
forum: General Help
---

### Post by krelverehan on 2007-10-19
I own this 160gb external hdd and it is currently formatted using the standard ext2 filesystem. Is it possible to reformat it as a NTFS for easier use on Windows machines? Or at least create a partition half ext2 / half NTFS ?

Are there any programs that I could meddle with?

This is purely for fun. There is no serious data on this hdd.

Thanks!

---

### Post by dcstar on 2007-10-19
> **krelverehan said:**
> I own this 160gb external hdd and it is currently formatted using the standard ext2 filesystem. Is it possible to reformat it as a NTFS for easier use on Windows machines? Or at least create a partition half ext2 / half NTFS ?

Are there any programs that I could meddle with?

This is purely for fun. There is no serious data on this hdd.

Thanks!

You can reformat it to whatever you like, to as many different partitions as you like - that is what the gparted package does.

---

### Post by krelverehan on 2007-10-19
Thanks David. I'll give it a whirl.

---

### Post by krelverehan on 2007-10-19
Another question:

Now that I have a NTFS partition on my hdd, how do I can I make it so I can read/write it? Even as root it says it is a read only drive.

Thanks,
-KV

---

### Post by davidjmayo on 2007-10-19
use ntfs-3g which is in add/remove or synaptic or use apt-get or aptitude to install it.

---

### Post by krelverehan on 2007-10-19
Actually, after I posted that I decided "Why don't I doing what everybody always asks you to do before posting and try searching the forums for an answer"? And I stumbled upon this handy thread: 

**[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)]("http://ubuntuforums.org/showthread.php?t=217009")**

Thanks, though. I'll learn one of these days.

-KV

---

