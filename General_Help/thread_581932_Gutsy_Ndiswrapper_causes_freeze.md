---
title: "Gutsy Ndiswrapper causes freeze?"
date: 2007-10-19
forum: General Help
---

### Post by Onay on 2007-10-19
So I got the latest ndiswrapper (1.48) source code and I compiled it in my new Gutsy installation, and the drivers installed fine. I load the module to the kernel, and everything is going smoothly. Now, though, when I try to connect to my wireless router (encrypted with WEP-64 bit) which worked fine in Fiesty, the network manager attempts to connect for a second or two, then the entire desktop freezes. Mouse doesn't work and I can't even restart X.

Is this an Ndiswrapper problem, a Network Manager problem, or a Dbus problem? Or could it be something else?

I have tried a make uninstall and make distclean before recompiling and the same problem keeps occuring. I'm afraid that if I save my aliases with ndiswrapper -m then the system won't boot up at all. Anybody got any idea?

By the way I'm in my old Fiesty installation now so if you ask me to test certain things it might take me some time to reply, since I'd have to reboot to try it. Thanks everyone.

---

### Post by Onay on 2007-10-19
Bump

I even tried to connect to other networks and using different settings (128 bit or closed system instead of open 64) and still the same thing is happening.

Is the latest ndiswrapper not supposed to work with Gutsy?

---

### Post by Onay on 2007-10-19
Bump...

---

### Post by Onay on 2007-10-19
Uggh no ideas? Gutsy is useless without internet...

---

### Post by Onay on 2007-10-19
I'll post another in the beginners section....

---

