---
title: "Lenovo laptop won't stay shut off, boots up after shutdown"
date: 2013-09-03
forum: General Help
---

### Post by CaptSaltyJack on 2013-09-03
I have a ThinkPad S431 running Ubuntu 13.04, and it won't shut off by conventional means. When I choose shutdown, the machine turns off but then promptly turns back on again right away. In order to turn the computer off, I have to reboot, go into the BIOS, then press the power button, after which the machine turns on *again*, then I go into the BIOS again and press the power button, and then it stays off.

If I turn the computer on and go into the BIOS right away and press power, it turns off properly. It seems that the problem arises after having booted into Ubuntu.

I've already tried adding acpi=force in the grub startup command line and it didn't do anything. Does anyone know how I can troubleshoot and resolve this?

---

### Post by blackbird34 on 2013-09-04
Have you tried doing it by command line?

```
sudo shutdown -h now
```

---

### Post by CaptSaltyJack on 2013-09-04
I have, yes. Didn't work either.

---

### Post by RodK on 2013-09-05
How about pulling the plug out of the wall? Do you reboot after that?

---

### Post by CaptSaltyJack on 2013-09-05
That doesn't work either. Actually I think I've figured out this might be a UEFI issue. I'm going to submit a bug on this.

---

### Post by CaptSaltyJack on 2013-09-05
Oh well what do you know, this is fixed in kernel 3.8.0-30! :)

EDIT :Nope, never mind.

---

