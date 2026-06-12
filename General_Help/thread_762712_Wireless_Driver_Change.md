---
title: "Wireless Driver Change"
date: 2008-04-22
forum: General Help
---

### Post by Exsecrabilus on 2008-04-22
Ubuntu 8.04 switches from bcm43xx-fwcutter to b43-fwcutter.

What's the difference? Is the second one better?

---

### Post by Ayuthia on 2008-04-22
Actually, it was not Ubuntu that made the change.  The developers of bcm43xx made this change when kernel 2.6.24 was introduced.  They have now depreciated bcm43xx and made b43 and b43 legacy.  The 4301, 4303 should be using b43legacy.  The 4306 and 4309 cards with revisions less than four should also be using b43legacy.  b43 should be used for the other ones.

I think that the b43 driver is an improvement overall for most of the cards.  My card (4311 rev 01) has a better bit rate and has better transmission using b43.  However, not everyone has the same results.  I have seen that the 4306 and 4312 owners have some issues with the new drivers on Ubuntu (There was a patch used that fixed it, but it broke the other drivers).  I have also heard that the working patch is in 2.6.25 but I have not heard what is going to be done with the 2.6.24 kernel.

Overall, the b43/b43legacy drivers will improve over time, but the bcm43xx driver work has stopped.

If you want to read more about the driver, you can go to [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43)

---

