---
title: "remote control xubuntu to xubuntu; what are my options?"
date: 2007-02-24
forum: General Help
---

### Post by ffxr on 2007-02-24
hi..

i want to remote control a xubuntu box, i have sitting in the other room..  from another xubuntu box over my wireless network...

i have wondered through many threads on this subject, & the only options i see are VNC based.. i tried this but i do not want it to take completely over my local desktop.. i want to be able to view my remote desktop in a window on my local desktop...

i want something preferably lightweight and easy to setup, (its only a temporary thing while i setup the other machine up & migrate my live data to it)

can anyone suggest any other methods...?

thanks.

---

### Post by ffxr on 2007-02-24
it appears you can get a window of the remote desktop with vnc.. does anyone know how something like this was achieved?

[http://en.wikipedia.org/wiki/Image:Kde_Vnc_01.png](http://en.wikipedia.org/wiki/Image:Kde_Vnc_01.png)

---

### Post by Scunizi on 2007-02-25
I'm not sure exactly how, but try to search the forums for ssh with x.

---

### Post by Mets on 2007-02-25
Well, if you just want to run programs off of that box on your computer, without taking up your computer's resources, than X-forwarding is the best way to go.  That's just a simple "ssh -X username@yourbox" and you are in and running with X.

Remote desktop is really a Windows thing because Windows doesn't have an equivalent to X-forwarding.  Forwarding X is faster and better, and you typically use remote desktop on linux to pipe into a Windows machine.  No idea what programs Xfce supports, but KDE has Remote Desktop (OT).

---

