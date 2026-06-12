---
title: "reconfiguring xserver?"
date: 2007-04-25
forum: General Help
---

### Post by SimpliciTy on 2007-04-25
ok so i had a that wouldn't let me get a log in screen once i updated from ubuntu 6.10 edgy to 7.04.
we determined all i needed to do was enter in recovery mode and reconfigure xserver
so i ran
```

sudp dpkg-reconfigure xserver-xorg

```

and that came up with the reconfigure screen with no problems i go through reconfiguring everything up untill when i have to select my color depth.
i select the highest since i have a somewhat high performance gfx card (nvidia 7600gt)
and when i go to select 24 bit (the highest allowed) i press spacebar to select, press my arrow key to press ok and once i press ok the recovery console shows up at the bottom of the screen and says something like warning overwrtiting a custom config, the back up will be place in blah blah blah.
then i have the option to enter a command but there is no way to go back the the configurer!
i tried rerunning the code but that brought me back to the begging and said the same thing.
i can't figure out how to get back to the xorg configurator.
please help.
thanks,
Simplicity

---

### Post by SimpliciTy on 2007-04-25
please help.
i really need to atleast get my homework files onto a cd.

---

### Post by dreadlord_chris on 2007-04-26
> **SimpliciTy said:**
> please help.
i really need to atleast get my homework files onto a cd.

LOL... it did that because you had finished the configurator. If you set everything right you should be able to reboot into your Desktop session.

---

