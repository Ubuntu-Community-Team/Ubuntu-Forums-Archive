---
title: "install tp-link drivers (from their site)"
date: 2016-01-28
forum: General Help
---

### Post by xp15 on 2016-01-28
Just discovered that tp-link made a driver for linux. I cant tell if it would be better that Pvaret's one, but it should, doesnt it?

Here is the download page (third option): [http://www.tp-link.com/en/download/TL-WN822N.html#Driver](http://www.tp-link.com/en/download/TL-WN822N.html#Driver)
The driver comes with a guide, but its not really clear what to do.

Pls help me figure it out, so me and other users can install it easily.

---

### Post by xp15 on 2016-01-31
bump

---

### Post by Vladlenin5000 on 2016-01-31
> **xp15 said:**
> Just discovered that tp-link made a driver for linux.
No, they didn't. The chipset manufacturer did.

> I cant tell if it would be better that Pvaret's one, but it should, doesnt it?
Why should it be better than one that has been patched specifically for your system? However, if you mean [this one]("https://github.com/pvaret/rtl8192cu-fixes") which is old and unmaintained then most likely 15.10 already has better support natively.

> The driver comes with a guide, but its not really clear what to do.
Pls help me figure it out, so me and other users can install it easily.
If it's working then keep it.
The guide should be enough if you know what you're doing and it's clear you don't. It isn't pertinent or even remotely useful for regular users. If there are issues using this hardware or any other based on the same chipset, those can and should be addressed in a *per case* basis and not as generic, probably outdated, procedure (which, BTW, would be a copy of the guide) of compiling a driver written specifically for older kernels.
Again, any current Ubuntu should have better native support than anything from 2/3 years ago.

---

### Post by xp15 on 2016-02-03
The problem is that my device is disconnecting or that the signal is dropping, then I have to unplug it and pkug it bacl and play with it till it work normally again. for an hour or less.

---

### Post by Vladlenin5000 on 2016-02-03
I suggest you go to the Network & Wireless section, read [this sticky]("http://ubuntuforums.org/showthread.php?t=370108") and then open there a new thread explaining in detail what's happening and include the results of the script.

---

### Post by xp15 on 2016-02-04
ok. thanks.

---

