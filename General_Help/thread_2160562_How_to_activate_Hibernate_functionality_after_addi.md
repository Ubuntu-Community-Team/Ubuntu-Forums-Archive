---
title: "How to activate Hibernate functionality after adding more Swap space ?"
date: 2013-07-07
forum: General Help
---

### Post by jdackle on 2013-07-07
*Using Xubuntu 12.04 LTS Precise Pangolin*

Brief description of what I did so far :
I had a 4GB Swap partition (old disk from old setup) on a (new) 8GB RAM system.
I created a new 16GB Swap partition, which is active on my system.

Now for the hibernation functionality. From the community's SwapFaq on [https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F) :> Making the swap partition work for hibernate (optional)

'INFO: This will not work for 12.04, resume from hibernate work differently in 12.04.' So... how do I activate the Hibernate functionality with this new Swap space?

---

### Post by 2F4U on 2013-07-07
Hibernation shouldn't be affected by your setup. However, hibernation has been deactivated in Ubuntu 12.04. If you want to reactivate, follow the official guide:

[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

---

### Post by jdackle on 2013-07-07
LOL. Guess I might have searched a bit more myself.
Thank you so very much! :)

---

### Post by jdackle on 2013-07-08
Actually...
That link about reactivating Hibernate on 12.04 didn't help - my system failed the tests.
However following the instructions on the link I had posted above and which were said not to work on 12.04 ... WORKED PERFECTLY! :lol:
Go figure!...

---

