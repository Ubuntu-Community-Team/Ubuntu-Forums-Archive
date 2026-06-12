---
title: "Unable to resize ext3 on fake Raid"
date: 2008-05-21
forum: General Help
---

### Post by Stason on 2008-05-21
I am running 7.10 on fake RAID

Here is what my partitions look like (ignore the LOCK signs as they are not present when I boot from LiveCD):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=70977&stc=1&d=1211375047[/IMG]

I want to increase ext3 to occupy the unallocated space.

Booting from liveCD and running gparted from the window shown above I get this error:

======
Filesystem mounted or opened exclusively by another program?
e2fsck: Device or resource buzy while trying to open /dev/mapper/....
======

If I enter into the ext3 partition using the menu on the top right - I cannot resize it, it says there is no space.

I am utterly confused now as to how this works, as I spent days trying to figure it out with no luck at all. Any help would be appreciated.

---

### Post by fjgaude on 2008-05-21
Gosh, you are pushing the envelop likely further than the developers ever tested and designed for.

Gparted doesn't like raid... dmraid is something few use.

The ext3 partition could be an extended one and I don't think gparted handles such, i.e., able to expand. What does the information menu, show features GParted, show as to what it can do? It doesn't like NTFS, and I think that's really the same with extended partitions. The fourth (usually) and higher partitions are extended. There can be only four prime partitions.

Keep us in the loop as to how you are doing.

---

### Post by Stason on 2008-05-21
May be I wasn't completely clear, but there is one way to increase that ext3 partition, i.e. to delete it and to format a new larger one. Unfortunately this means reinstalling Ubuntu from scratch, since restoring the image also restores the old size. Given the amount of time it takes to configure ubuntu I am in need for a comprehensive way to increase that ext3 partition without destroying data on it.

Stupid question, but I am really desperate - if I just make a backup (not image), reformat and copy the backup to that new larger disk - will it boot?

---

### Post by fjgaude on 2008-05-21
Likely not... I haven't ever tried that but it all has to do with where Grub is pointing to, and from what drive grub is located upon, i.e., the boot loader.

You might try it, it might work...

---

