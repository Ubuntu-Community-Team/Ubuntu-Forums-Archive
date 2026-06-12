---
title: "Ext3 partition private in Windows?"
date: 2008-05-15
forum: General Help
---

### Post by 1002285 on 2008-05-15
I use both Windows and LinuxMint on my computer, and my documents are on a partition that is separate from both systems. This partition has ext3 file system and I use this partition from Windows with this driver: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html).

I tried, in Windows, to make my user's home folder on that partition private, so that for example Guest user in Windows could not access it. In the sharing options box, I am not able to check the box "Make this folder private". Is it possible at all?

If not, are there any ways to have a guest account in Windows so that the person logging into that account cannot access the ext3 partition or parts of it?

---

### Post by OzzyFrank on 2008-05-15
I'm afraid I can't help, but had to stop and ask:

**Have there been any issues using this ext2 driver with ext3 partitions?** I've seen mention of being wary of this, since using something that works with ext2 could do damage to an ext3 partition. I assume you have enabled full write access to the Ubuntu partition, so you seem to be the best person to ask. Cheers

---

### Post by chrisccoulson on 2008-05-15
I don't think you can do this in Windows because it doesn't understand the Linux file permissions

---

