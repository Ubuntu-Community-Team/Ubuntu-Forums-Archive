---
title: "Muon: This operation cannot continue since proper authorisation was not provided"
date: 2013-03-09
forum: General Help
---

### Post by Statia on 2013-03-09
Kubuntu 12.04.2, KDE 4.10.1
It used to be that I could open Muon updater, let it check for updates, click install when updates were found and then it would ask for my root password.
Now when I click install I get a dialogue box:

```
This operation cannot continue since proper authorisation was not provided
```

I googled it and can find it as a bug dating back to 2011 and early 2012, but not to recent date.
Some of the earlier solutions point to having polkit-kde installed, but I have that:

```
root@quokka:/home/statia# dpkg -l | grep polkit-kde
ii  polkit-kde-1                                                      0.99.0-3ubuntu5                                      KDE dialogs for PolicyKit
```

I can probably work around this by running Muon updater with kdesudo, but I'd rather have it fixed.
Anyone any ideas?

---

### Post by Statia on 2013-03-12
BONK?
No, what's it called?
BUMP!
That was it!

---

### Post by Statia on 2013-03-16
Bump

---

### Post by Statia on 2013-03-18
And just as mysteriously as it stopped working, it has started working again.

---

### Post by oygle on 2013-04-16
I had this message today. I did the "check for updates" again, but same message.

The updates are security updates, but I can't install them.   :(

---

### Post by Statia on 2013-04-29
> **oygle said:**
> I had this message today. I did the "check for updates" again, but same message.

The updates are security updates, but I can't install them.   :(

You can do your updates from the command line, with sudo apt-get update followed by sudo apt-get upgrade.

---

### Post by oygle on 2013-04-30
Yes, I think that is what I did to get rid of the message.

---

