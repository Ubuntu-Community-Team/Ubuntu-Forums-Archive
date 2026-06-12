---
title: "High IOWAIT on tmpfs"
date: 2013-08-09
forum: General Help
---

### Post by wkuhns on 2013-08-09
I have a Core2 Quad (Q9300) with 8gb RAM. I'm running Xubuntu 12.10 with kernel version 3.5.0-37-generic. The /home directory is mounted via NFS from a server running Xubuntu 12.04.

I had a problem with intermittent browser and/or desktop 'freezing'. I traced it to high IOWAIT by chromium-browser writing to cache on the local machine and jbd2 writing to the journal on the /home partition on the server. OK, only an idiot would set up browser cache on an NFS volume. Easily fixed - I set up a 512mb ramdisk (tmpfs) for my Chrome browser cache.

The server is happier and the intermittent freezes aren't as bad, but they still happen. When they do, it's still the browser pegging IOWAIT at 99+% writing to the ramdisk.

How can you get massive IOWAIT writing to a ramdisk? What can I try next? is this a kernel issue or a chromium-browser issue?

---

