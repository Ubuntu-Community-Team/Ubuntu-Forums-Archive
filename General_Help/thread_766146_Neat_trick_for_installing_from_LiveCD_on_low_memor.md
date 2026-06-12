---
title: "Neat trick for installing from LiveCD on low memory systems...."
date: 2008-04-25
forum: General Help
---

### Post by natrixgli on 2008-04-25
Lo and behold: I actually got inspiration from Vista!

Feel free to laugh, but I recently installed Gutsy on a laptop with only 256mb of RAM....and was far too impatient to download the alternate installer CD. I already have a bootable USB drive that I like installing from 'cause it's much faster than the CD in most cases. 

Needless to say it was painfully slow. Since I have little or no patience, I had an idea... Speedboost, as they call it in Redmond, WA.

I grabbed another 1GB USB drive, backed it up, and formatted it as swap using parted on another system.

Then, after booting the liveCD, I tossed it in, and in a terminal, typed 'swapon /dev/sdx1' (of course sdx1 was really sdb1, but this can vary depending on your configuration..) 

It made a massive difference. The install went much more quickly this way!


Dare I say that Vista actually contributed something positive to my computing experience??

-n8

---

