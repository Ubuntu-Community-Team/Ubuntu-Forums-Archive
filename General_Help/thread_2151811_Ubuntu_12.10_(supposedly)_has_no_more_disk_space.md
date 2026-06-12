---
title: "Ubuntu 12.10 (supposedly) has no more disk space?"
date: 2013-06-05
forum: General Help
---

### Post by LaizureBoy on 2013-06-05
Hello, I made a Ubutnu 12.10 partition of about 250 GB's, and when I try to move anything for use with Wine above 3 or so Gigs, it says there is insufficient space on the harddrive to do so.

I know this is not the case, as a quick check of "df -h" identifies the hard drive not being at fault.

Can anyone help me out on this?

---

### Post by vamped on 2013-06-06
It sounds like you are trying to move a single file larger than ~3 Gb. Is this correct? What file system did you format on the partition? FAT partitions have a limit of 4 Gb I believe. Ext_ partitions have no such limit.

---

### Post by 3rdalbum on 2013-06-06
Can you please show us the output of df -h?

And can you please confirm that you booted from the Ubuntu CD and installed Ubuntu that way? Or did you use Wubi? (the installer that runs in Windows)

---

