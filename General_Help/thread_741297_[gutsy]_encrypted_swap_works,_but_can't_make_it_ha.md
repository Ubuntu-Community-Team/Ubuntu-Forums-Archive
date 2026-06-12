---
title: "[gutsy] encrypted swap works, but can't make it happen on boot"
date: 2008-03-31
forum: General Help
---

### Post by shadowfirebird on 2008-03-31
I've set up encrypted swapfiles using cryptsetup.  It works fine, but when I boot I have to:
> sudo /etc/init.d/cryptdisks start
> sudo swapon -a

...to get it to work again.

Anyone got any ideas?

---

