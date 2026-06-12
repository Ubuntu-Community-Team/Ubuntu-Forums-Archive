---
title: "Finding more information about crashes"
date: 2008-04-20
forum: General Help
---

### Post by lxowle on 2008-04-20
Hi,

I use hardy heron, and with the latest updates, it crashes all the time. I can still move the mouse, but everything else is frozen.

I don't have a problem with this - it is beta software, but I wondered if I could find out what is causing the crash. It doesn't seem to be firefox, I can be doing anything, and the screen just freezes.

I've checked the system logs - and they seem normal - is there anything else I can do to see what might be causing the problem?

The original beta install of heron works fine, and when I dual boot to windows, that works fine as well.

Thanks for any advice.

---

### Post by pointone on 2008-04-20
X related errors will be logged in "/var/log/Xorg.0.log".

---

### Post by lxowle on 2008-04-21
Thanks for that - it doesn't seem to be the problem, or at least, any problems are not being recorded in that log prefixed by (EE).

Given that the mouse still moves, but everything else is frozen, does that tell me anything?

---

### Post by pointone on 2008-04-21
Can you still press Ctrl+Alt+F1 to access a the command line when it's "frozen"? If so, try running "top" to see if there's any process using up all your resources.

---

### Post by -Zeus- on 2008-04-21
you can go to System > Administration > System Log

---

### Post by lxowle on 2008-04-26
Thanks to everyone that replied.

I checked all the logs, and there were no suspicious errors recorded there. Also, the keyboard is completely frozen during a crash, but the mouse still moves.

Anyway, it was so bad I had to stop using ubuntu- it was crashing perhaps every 5-25 minutes or so. 

Today I downloaded and installed the 64bit bit version of ubuntu for AMD computers - and so far everything seems ok. Perhaps it was too many upgrades using the beta distributions which somehow caused the problem?

It would have been good if I could have tracked down what was causing the problem - I'm surprised that it is not easy. Nevertheless, I'll be content if the problem just goes away with my new install.

Thanks again everyone,
lxowle.

---

