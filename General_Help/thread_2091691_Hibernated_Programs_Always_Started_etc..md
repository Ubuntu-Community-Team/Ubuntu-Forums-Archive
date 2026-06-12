---
title: "Hibernated Programs Always Started etc."
date: 2012-12-05
forum: General Help
---

### Post by Martom on 2012-12-05
Hello all,

I enabled hibernation on my Xubuntu 12.10 installation as per this documentation:

[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

It seemed to sort of work: I had a Terminal and a Firefox window open, I hibernated my laptop, restarted and there were my windows, as expected. However, what I was doing in those programs was not loaded; I just got fresh windows. 

Furthermore, I now have an odd side effect: every time I log into Xubuntu, it automatically starts up a Terminal and Firefox. To clarify, I'm talking about a fresh boot after the machine has been powered down, left for the night, booted into Xubuntu,  booted into Windows, booted into Xubuntu etc. It still keeps doing it. They're just fresh windows, e.g. Firefox doesn't have any sites open but just goes to the start page. I checked my startup programs and neither of them are listed.

It gets worse, too. Now, hibernation doesn't work anymore! When I try to hibernate, nothing happens. When I go pm-hibernate, nothing happens (no output either.)

I'm at a loss. Does anyone know what's going on here?

---

### Post by Martom on 2012-12-06
I've been fooling around some more and I noticed that Suspend is not working either; nothing happens when I try to make Xubuntu suspend, except that my desktop partially freezes. At first I was unable to open the User menu in the top right corner, so I couldn't log out or reboot. Then gradually the entire system just froze up.

Can anyone help me? The ability to suspend and hibernate is not a priority, but the programs starting up when I log in are highly annoying.

---

### Post by bryncoles on 2012-12-06
Hi Martom

I think you accidentally checked 'save sessions' when you logged out.  Try this:  open settings manager (mouse icon -> settings -> settings manager) and select the session and startup tab.  Tick 'automatically save session on log out'.  Close all programmes.  Log out and log in again go back to the session manager and untick 'automatically save session on log out'.  That should fix it!

---

### Post by Martom on 2012-12-06
Hi bryncoles,

I forgot to mention this, but I already checked this and I do not have this setting ticked.

---

### Post by Martom on 2012-12-06
I suppose things have a way of solving themselves, sometimes... Somehow, my Suspend and Hibernate are working fine now. I have no idea what changed, I've been fiddling with other things all day and decided to give it a go just now. Perhaps one of today's updates fixed something.

The problem with the programs starting up was due to my misinterpreting how the session saving worked. I expected it to save a session and the load it the next time only. Xubuntu, however, loads that session every time, for some reason.

Thanks!

---

