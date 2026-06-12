---
title: "Enforcing a service startup order (Bluetooth)"
date: 2007-06-02
forum: General Help
---

### Post by kidders on 2007-06-02
Hi guys,

This is more of a minor inconvenience than a real problem, but I'm interested in your recommendations...

I'm using bluetooth input devices on my box so, as you might expect, if they haven't started talking to it by the third time X tries to start, I wind up having to log in, type my password, do a **sudo /etc/init.d/gdm restart**, and type my password *again* ... which gets annoying.

[COLOR=RoyalBlue]What I've done[/COLOR] is created an /etc/init.d/btattach, that searches a few times, until it's found both a keyboard and mouse ... something I'm finding much more reliable than what I get when I alter HIDD_OPTIONS in /etc/default/bluetooth. The problem is that I can't find a way of forcing X to wait for that service to start.

[COLOR=RoyalBlue]What I'm *not* willing to do[/COLOR] is alter /etc/init.d/gdm (which is, of course, the easy way out!), because I don't want a future non-interactive **apt-get upgrade** to refuse to replace it. I'm assuming that's what the default action would be, in the event it wanted to delete a file in /etc that had been modified by something other than Ubuntu's package manager.

I'm sure there must be a "right" way to enforce a particular service startup order, or modify system scripts safely, that I just don't know about, so I won't be offended if the first response I get is "RTFM, you fool!". :-) I'm well used to Linux, so I feel like I should know this one by now!

Thanks for your time.

---

