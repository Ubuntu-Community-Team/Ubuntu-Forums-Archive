---
title: "xubuntu 18.04 auto login wanted - not asking password, still presents log-in dialog"
date: 2020-01-15
forum: General Help
---

### Post by wb0gaz on 2020-01-15
I have installed xubuntu 18.04 and completed updates to current version (1/15/2020). This is still a fresh install (just install, updates, and my attempts to set auto log-in unsuccessfully). This is xubuntu, not ubuntu (!).

I want auto-login (which I did not select during install.)

I went to settings > users and groups > password and set the tick box "don't ask for password at login" and the machine does not ask for password at log in, but it still presents a (very unwanted) login dialog box between startup time and desktop visible.

I am since making this change also getting "system problem detected" nag screen at each startup (which I can cancel or accept, but no details are offered so I cannot tell what is happening.) If unrelated to auto login problem, how do I deal with this repeated nag screen?

What is happening and how can I get this to behave?

Do I need to go back and do a whole new install and set auto login?

Why is this not a simple, obvious configuration step?

Thank you!

---

### Post by CelticWarrior on 2020-01-15
The "system problem detected" is probably unrelated.

Regarding your issue, sorry to say, it's working as designed. First of all you really **should** have a password but when you decide against the best practice the system will ask you anyway right after opening your session in order to open a special database where, among other data, your WIFi passwords are stored. There's no safe way around this and even Microsoft has been forcing the login with password for years in Windows 10. Keep in mind it's for your own safety.

---

