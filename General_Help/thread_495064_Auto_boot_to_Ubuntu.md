---
title: "Auto boot to Ubuntu"
date: 2007-07-07
forum: General Help
---

### Post by seraphlm on 2007-07-07
Hey, I've just installed Ubuntu using Wubi and it was great. It was so great that I've been thinking of using Ubuntu as my main OS. Is there anyway to put Ubuntu as the default OS during the OS select? Thanks!

---

### Post by tuxcantfly on 2007-07-07
In ubuntu, open up /media/host/boot.ini, make sure to back it up first though in case something screws up.

there will be a line that says "default=something", like:

```
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
```

change that to:

```
default=C:\wubildr
```

or whatever the last line begins with, if it's an older version of wubi, it might be C:\grldr

you can also change the timeout line by changing the line that says "timeout=something"

once you're done save and reboot, if something screws up, just revert to the boot.ini you backed up

---

