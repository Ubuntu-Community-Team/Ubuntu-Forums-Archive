---
title: "Steam Help"
date: 2015-12-09
forum: General Help
---

### Post by adam175 on 2015-12-09
Not sure if this is the right section of the forum I should be posting this to (sorry, I'm new...) but recently I've run into some problems with Steam, as my computer is 64Bit and it looks like Steam only supports 32Bit (?) I've tried some work arounds, but to no avail, does anyone have a way I would be able to run Steam without resorting to Wine? ```
Running Steam on ubuntu 15.10 64-bitSTEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast



```

Any help would be appreciated, Thanks!

Adam.

---

### Post by QDR06VV9 on 2015-12-09
This worked for me..
```
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libgcc_s.so.1
```
Sometimes the second line shows a not found.
Regards

---

