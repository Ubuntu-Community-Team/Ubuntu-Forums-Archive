---
title: "My system reboots when I shut it down [14.04]"
date: 2014-08-17
forum: General Help
---

### Post by nitin.mahendru88 on 2014-08-17
HI Everyone,

When I try to shutdown my system via command line( sudo shutdown -v now) my system just reboots back up again.

When I try to normally shutdown using the gui interface on unity, it's stuck on the purple ubuntu screen.

I really don't know what more information to share. Request your help to point me and I'll share logs which might help.

I am using 14.04 on a lenovo Y540 laptop.


Thanks in advance..!

---

### Post by egeezer on 2014-08-17
I'm not familiar with -v used with shutdown (verbose?), but you might try sudo shutdown now -h -P (halt and powerdown).

---

### Post by nitin.mahendru88 on 2014-08-17
> **egeezer said:**
> I'm not familiar with -v used with shutdown (verbose?), but you might try sudo shutdown now -h -P (halt and powerdown).

thanks a lot.. this works..! :popcorn:

and now I can shutdown normally too and it works.

Forum Moderators,
Let me try using this for a week before we can mark this down as solved or closed.

---

