---
title: "Ubuntu 21.10"
date: 2021-11-03
forum: General Help
---

### Post by Bejje on 2021-11-03
I just installed Ubuntu 21.10 on an old HP laptop that is probably 6 years old. Before that I hade Windows 10 2104 on it. Worked fine.
But after install to Ubuntu it fails to boot. I tried reseting Bios settings to default, then running the setup again, but it fails to boot again.

I was expecting this on a brand new laptop, but not one that is 6 years old, that would boot right away, but not this one.
It has an SSD and was modern for it's age, but cannot boot Ubuntu for some reason.

Any idea what to do about that? I would tell you what the model is, but it does not show underneath it as normal laptops, so I would have to install Windows again to get that info from software.

---

### Post by QIII on 2021-11-03
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2468548").

Please do not hijack the threads of other users.  Those users deserve one-on-one attention for their issue, just as you do for yours.  Further, while symptoms often appear to be the same, they may stem from vastly different underlying causes.

---

### Post by GhX6GZMB on 2021-11-03
How did you install Ubuntu? USB-stick, DVD? How did you create those?

---

### Post by oldfred on 2021-11-03
Many with HP have had to update UEFI and if SSD, update SSD firmware.
And then they only could reset boot order to have Ubuntu first by using UEFI settings & boot tab (not UEFI boot menu).
Grub uses efibootmgr to install UEFI entry & set Ubuntu as first in UEFI boot order. But most HP seem to auto reset boot order.

To see boot order & details
sudo efibootmgr -v

---

