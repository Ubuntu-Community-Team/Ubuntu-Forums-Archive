---
title: "Is there a Sleep/Power Off Timer function for Ubuntu?"
date: 2007-08-18
forum: General Help
---

### Post by wersdaluv on 2007-08-18
Before I sleep,  I want my computer running for a while for it to play music. The problem is, I have to turn off my computer because I don't want it running all night long.

TVs have a sleep timer function that turns of the machines whenever it is left unattented for a period of time. 

I want my Ubuntu machine to automatically turn off after a certain period of time for me to afford sleeping while my computer is running.

How do I enable that function?

---

### Post by logos34 on 2007-08-18
run this command in a terminal:

**sudo shutdown -h hh:mm ** [*specific time in future, 24hr clock, hour minute*]

**sudo shutdown -h +m**  [*where m=minutes from now*]

[edited]

[http://linux.about.com/od/commands/l/blcmdl8_shutdow.htm](http://linux.about.com/od/commands/l/blcmdl8_shutdow.htm)

---

### Post by wersdaluv on 2007-08-19
> **logos34 said:**
> run this command in a terminal:

**sudo shutdown -h hh:mm ** [*specific time in future, 24hr clock, hour minute*]

**sudo shutdown -h +m**  [*where m=minutes from now*]

[edited]

[http://linux.about.com/od/commands/l/blcmdl8_shutdow.htm](http://linux.about.com/od/commands/l/blcmdl8_shutdow.htm)

Kewl.

:KS

Thanks!

How about a GUI way?

:guitar:

---

