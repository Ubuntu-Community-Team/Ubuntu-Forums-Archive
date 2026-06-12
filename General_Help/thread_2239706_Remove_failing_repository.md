---
title: "Remove failing repository?"
date: 2014-08-15
forum: General Help
---

### Post by Mike_Walsh on 2014-08-15
Afternoon, all.

Now then; I've got a little bit of a problem that I need some advice on. Sorry, admins, if this is in the wrong forum, but I wasn't too sure where to put this...

I've had the yellow warning triangle showing in my taskbar for the last couple of weeks. Every day when I log in, it's not showing for about an hour, then up it pops.

I've tried all the suggested fixes from the drop-down menu; "Show updates, Check for updates, watch for failing repositories, etc..." Nothing seemed to shift it.

I finally tracked it down to this repository:- [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) - hand

I'd installed this a couple of months ago, when I was trying to multi-install several distros onto a large USB stick I have, a 64 Gb one. I've since given up on that idea, as I've grown more comfortable with using GParted and some of the other disk management tools, and they've all gone on my external Seagate HD.

I've gone into 'Software and updates', and unticked the box for this repo in the 'Other Software' tab. Touch wood, it appears to have solved the problem; but I can't yet say with any certainty whether it's a permanent fix.

Having refreshed the cache, I see this repo is still there, although un-checked. Do I need to do anything else to completely remove this entry from the system, or will what I HAVE done be sufficient?

Any advice would be appreciated.


Regards, 

Mike.

---

### Post by Karlchen on 2014-08-15
Hello, Mike_Walsh.

As you have disabled the offending repository, it will never be queried again. As you can still see the entry, only unticked (disabled), you could enable it again. So it is not gone. In order to remove the entry completely, I would launch Synaptic => Settings => Repositories => Other Software. In the list mark the offending entry. Click the button [Remove].

Kind regards,
Karl

---

### Post by Mike_Walsh on 2014-08-15
Hi, Karlchen.

Thanks for that; worked a treat. 

Actually, I could have gone straight to Software & Updates via the Dash, but anyway...thanks for the tip. I'll remember that for future use.

Appreciated. I'll mark this one 'solved'.

Regards, Mike.

---

