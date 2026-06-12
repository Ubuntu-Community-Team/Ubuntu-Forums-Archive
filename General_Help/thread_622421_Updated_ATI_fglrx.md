---
title: "Updated ATI fglrx"
date: 2007-11-24
forum: General Help
---

### Post by bkraptor on 2007-11-24
When are we to expect an update for the fglrx driver in Gutsy? 8.42.3 (7.11?) has been released for a while now and it hasn't been pushed through update yet, even though it fixes AIGLX and hibernate/suspend for some. Any word from the developers?

I don't really wanna go messing with installing the driver manually as I figure it will come as an update anyway.

---

### Post by hardyn on 2007-11-24
ubuntu is not "rolling release" software. the driver that was shipped, is usually the driver that stays.  You will probably have to install the driver manually.

---

### Post by bkraptor on 2007-11-24
Even though it's obvious the driver is broken by the new kernel?

I really can't believe this to be the official stance.

<edit>
Is there any written official response regarding this issue?

<edit #2>
I've just manually installed the drivers provided by ATI and they don't fix the suspend/hibernate problem. Bummer :(

---

### Post by hardyn on 2007-11-25
basicly there is no offical stance with a closed sourse package... the driver is ATIs problem, not ubuntu or linux in geneal.  To keep the packages manageable, the ubuntu developers have chosen to stayed with a fixed release schedual.  you usually get a new driver every 6months with each OS release.

I there are LOTS of work arounds for the FGLRX driver, i have had it hybernating on my machine.  But it will up to ATI to either fix the problem or open source to the driver.

---

