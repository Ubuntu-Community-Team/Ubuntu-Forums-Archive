---
title: "Login issue after upgrade to Xubuntu 13.10"
date: 2013-11-29
forum: General Help
---

### Post by motorcity909 on 2013-11-29
HI there

I upgraded from Xubuntu 13.04 to 13.10 yesterday and all went fine but now whenever I start or reboot my PC, a terminal command screen appears before my desktop asking me to login in to tty1 and I have to then type my login name and password.  After that it shows "name@name:~$" just like in a terminal, then after a few seconds boots to my normal desktop.

I never had to type any of that before (my PC is also set to auto-login as the only user so I don't have the normal Xubuntu login screen)

Once on my normal desktop, if I run the 'who' command, it shows there is tty1 *and* tty7.

I'm wondering if this is a graphical issue?  I'm using the same Nvidia driver (319) as I was pre-upgrade.

This is more of an irritant than a show-stopper but any help would be much appreciated as always.

Thanks
Dave

---

### Post by motorcity909 on 2013-12-03
Quick update.  Kinda fixed by accident.  Booted up my PC and didn't type  in login name & password immediately and after about 10-15 seconds,  it just carried on booting to my normal desktop.

The 'who' command only shows tty7, whereas before it was showing tty1 and tty7.

So not exactly fixed but absolutely fine now.

Cheers
Dave

---

