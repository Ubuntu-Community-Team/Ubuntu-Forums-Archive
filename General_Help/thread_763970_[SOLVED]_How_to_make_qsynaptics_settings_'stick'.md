---
title: "[SOLVED] How to make qsynaptics settings 'stick'?"
date: 2008-04-23
forum: General Help
---

### Post by ezramorris on 2008-04-23
Hi,
I use qsynaptics to adjust my touchpad settings, but is there a way to make these stay after a reboot. Every time i restart, i have to run qsynaptics, and then click OK.
Thanks.

---

### Post by spupy on 2008-04-23
> **ezramorris said:**
> Hi,
I use qsynaptics to adjust my touchpad settings, but is there a way to make these stay after a reboot. Every time i restart, i have to run qsynaptics, and then click OK.
Thanks.

You can enter the settings directly in /etc/X11/xorg.conf. The problem is that you need to know the correct syntax. :)

---

### Post by ezramorris on 2008-04-23
> **spupy said:**
> The problem is that you need to know the correct syntax. :)

That's the thing. It just defeats the objective of qsynaptics.

---

### Post by kellemes on 2008-04-23
Maybe this link helps?
[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

---

### Post by ezramorris on 2008-04-24
> **kellemes said:**
> Maybe this link helps?
[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

Thanks. I removed qsynaptics and installed gsynaptics, and using this, the settings stick.

---

