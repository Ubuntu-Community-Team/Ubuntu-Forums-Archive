---
title: "libconfuse0 goes missing..?"
date: 2008-02-29
forum: General Help
---

### Post by msarro on 2008-02-29
Just curious, I adore tilda and I found a modified version that doesn't give me the grey box bug. Well, last night I installed moblock, and after a reboot tilda wouldn't start. So, I tried to run it from the command line, and it started spitting an error that libconfuse0 was not installed. I mean, it was a simple enough fix (just an apt-get away), but still.. why?

Is there a reason why it would dissapear? So far as I know moblock doesn't use libconfuse, nor would it have a reason to uninstall it. So why would it spontaneously dissapear?

---

### Post by jre on 2008-03-02
I don't know confuse, but moblock (I make the debian packages and wrote moblock-control):
moblock does not use libconfuse. It only inserts some iptables rules and filters the traffic according to it's blocklist. So I don't see what could happen there.

Did I understand you correctly that everything worked again after you uninstalled moblock!?

Greets
jre

---

