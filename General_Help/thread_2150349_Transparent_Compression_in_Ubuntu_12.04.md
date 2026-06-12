---
title: "Transparent Compression in Ubuntu 12.04"
date: 2013-05-31
forum: General Help
---

### Post by Lysander10 on 2013-05-31
Hello everyone,

I'm running Ubuntu 12.04 server, and I'm looking for a solution to transparently compress files as they're written to/accessed from one of my hard drives. The standard solution seems to be fusecompress, but this package seems to have been removed from the repositories in 12.04. I've Googled for a solution, but to no avail (everything I found predated 12.04). I'm looking for up-to-date instructions on how to set this up. Any help would be greatly appreciated.

---

### Post by The Cog on 2013-05-31
The btrfs filesystem has a mount option for compression. You would have to reformat, and add the compress option to fstab.

---

### Post by Lysander10 on 2013-05-31
Thank you for the suggestion. Btrfs is a possibility, but this is running on a production server, and although we make regular backups, I'm not sure I feel comfortable using an experimental file system. Are there any other solutions?

---

### Post by Cheesemill on 2013-05-31
I use ZFS with compression on some of my machines, but they aren't Linux boxes (they run OpenIndiana).

You might want to look at ZFS for Linux but I can't remember if the Linux version supports compression or not.

According to this Wikipedia article ZFS and btrfs are the only two sensible choices for Linux.
[http://en.wikipedia.org/wiki/Category:Compression_file_systems](http://en.wikipedia.org/wiki/Category:Compression_file_systems)

---

