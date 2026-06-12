---
title: "Screen blank on resume"
date: 2014-05-28
forum: General Help
---

### Post by americast on 2014-05-28
Hi all,
  I have Xubuntu 14.04 LTS. It's working fine except for the fact that once the screen turns off for any reason what so ever, it does not come back to life again. For example, I close my the lid of my laptop. When I re-open it, the screen remains blank. The hard disk light keeps glowing. Even if the screen turns off because the PC was kept idle for sometime, the consequence is the same. I can't figure out what's wrong. Any help would be appreciated.

Thanx in advance...

---

### Post by paul142 on 2014-05-28
Have you tried pressing your power button for a moment to wake it up? Dont press too long or it will do a hard shutdown. If this is a continuing problem I'd change the power settings in the control panel so the display doesnt go into sleep mode.

---

### Post by slickymaster on 2014-05-28
This bug was fixed in the package **xfce4-power-manager - 1.2.0-3ubuntu5**.

Can you please post the output you get when you run in a terminal```
apt-cache policy xfce4-power-manager
```

---

### Post by pretty_whistle on 2014-05-28
I have this problem too but the updated power manager isnt showing up in synaptic package manager nor when I run software updater so I cant update. Cant get it via sudo apt-get install either.  

I will be watching this thread for solutions.

---

### Post by pretty_whistle on 2014-05-28
Update:

I went into software updater and changed the setting to get unsupported updates.  However, I don't know if that was necessary.  The important thing is I ran updater a few times and it found this update!  Solved!  :)

---

### Post by brian_woods on 2014-05-29
is it working good now? after updating software.i am also facing kind of same problem should i try it?

---

### Post by pretty_whistle on 2014-05-29
Yes it's working good now.  The update fixed it. :)

---

