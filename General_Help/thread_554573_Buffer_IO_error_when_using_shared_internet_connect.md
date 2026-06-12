---
title: "Buffer I/O error when using shared internet connection"
date: 2007-09-19
forum: General Help
---

### Post by eeeeepuk on 2007-09-19
Hi everyone. I've recently set up a new machine to act as a centralized server, with one of it's jobs to be to share an internet connection to another machine close by. Everything is absolutely fine with this machine, but the other machine is giving me problems.

It too works absolutely fine, except when sharing the internet connection from the other machine. When this is happening, after a while the system crashes, giving me "Buffer I/O error on device sda2, logical block [incrementing number series]" errors in the log. After maybe half a dozen of these and a couple of minutes later, I get a "EXT3-fs error {device sda1}: ext3_find_entry: reading directory" message, then the system (which becomes more and more unresponsive after the first set of messages) finally grinds to a halt.

This problem only occurs when using the shared internet conenction. Without it (or with the wireless connection direct) it is stable, and will stay up for several hours. With the shared connection a crash invariably occurs after an hour or two.

I've used the live cd to run fsck on the drive, and it reports no errors. Similarly, SMART reports that the hard drive is very healthy.

Can anyone suggest how I might go about resolving this problem?

---

