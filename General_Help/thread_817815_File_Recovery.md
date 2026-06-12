---
title: "File Recovery"
date: 2008-06-04
forum: General Help
---

### Post by jasonlfunk on 2008-06-04
I had a free partition on my laptop hard drive that I wanted to install Vista on. Little did I know that when I went to format the partition to NTFS, windows would decide to delete all of my logical partitions. :mad:

I have tried scanning the harddrive with gpart to try to restore them, but to no avail. The resulting tables were not the structure of the disk. 

As far as I know, the disc has only been mounted read-only since the partition table was lost. I'm at the point now where I just want to get the files I need off and start over. 

I "simply" need two directory trees /home/funkja and /var/www/ that should theoretically be all intact.

My question is this: What is the best tool to use to recovery these files? Would it be easy to boot with a live cd and mount an extra hard drive to move these too? I'd prefer not to take apart my laptop to remove my hard drive. Any advice would be most welcome.

---

### Post by HalPomeranz on 2008-06-04
You may be able to use the forensic tools on the Helix Live CD to recover your data:

[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

I warn you that this is not for beginners.  There are commercial data recovery services that you can use as well (Google for "data recovery").  Best of luck recovering your data!

---

