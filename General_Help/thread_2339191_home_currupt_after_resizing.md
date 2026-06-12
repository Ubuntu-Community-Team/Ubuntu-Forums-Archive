---
title: "/home currupt after resizing"
date: 2016-10-05
forum: General Help
---

### Post by BigYellowDog on 2016-10-05
I've resized my / partition and /home partition with gparted.  I've used gparted many times before without any issues, this time when I try to reboot Ubuntu I'm getting errors.

> 
blk_update_request: I/O error, dev sda, sector 662723776
ata1.00 exceptiob Emask 0x0 SAct 0x0 Serr 0x0 action 0x0 


It looks like my /home is the partition which is giving me problems, that was the one that I resized. 

Did another reboot, it's doing a fsck.  Is there anything else?

Can I somehow retrieve any data from that partition? If I can retrieve  any data how do I know whether or not the files are corrupt.

---

