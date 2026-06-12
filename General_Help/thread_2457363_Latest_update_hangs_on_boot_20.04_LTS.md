---
title: "Latest update hangs on boot 20.04 LTS"
date: 2021-01-31
forum: General Help
---

### Post by adedr on 2021-01-31
Edit: gave up trying fix - installed a new OS

Edit: this doesn't work now, but once resuming boot out of recory mode worked on the 3rd try. It failed to boot 10 times in a row before that. Doesn't work now and can't resume out of suspend

Running the 20.04.2 LTS. Applied the latest update when the dialog popped up. It said a restart was required. Did that, not it won't boot. Everything worked normally before that.
I can get to a command prompt in recovery mode, but no idea what to do.
What can I do to fix this?

System is an HP laptop.
Kernel is 5.4.0-65-generic
Based on stuff I've found online, I tried adding nomodeset to the boot line and that doesn't work

---

### Post by CelticWarrior on 2021-01-31
Welcome.

First things first, 'nomodeset' is not for such issues. Using randomly googled stuff that you don't understand the meaning, purpose or effects can make things worse than they already are.

> [COLOR=#000000]System is an HP laptop.[/COLOR]
Doesn't help. Please describe your hardware specifications, especially the graphics.
What exactly are or were you seeing when it "wouldn't boot"?
We may be able to troubleshoot from there.

---

### Post by adedr on 2021-02-01
Not sure exactly what info is important on system specifications
Hp pavilion laptop with intel i5
8gb ram
UHD 630 graphics and geforce GTX 1050 3gb

What other information is helpful and how can I find it?

For not booting, it gets to the grub menu, I select ubuntu, the next screen shows "HP" and "ubuntu" with a spinning progress indicator. The indicator stops and it just stays there. The fan starts running heavily.

---

### Post by CelticWarrior on 2021-02-01
OK, it's starting to make sense.

Did you installed Ubuntu with the option to install third-party drivers, etc.? That should have installed the required Nvidia proprietary drivers. And have you disabled Secure Boot in UEFI? That prevents loading unsigned drivers like Nvidia's.

Assuming all the above checks out, the problem now could have been triggered by a kernel update. Try booting a earlier kernel in recovery mode from the Grub menu.

---

### Post by Impavidus on 2021-02-01
Have you tried booting an older kernel?

---

### Post by adedr on 2021-02-01
Yes it was installed with 3rd party drivers.
Yes I disabled secure boot
The system was working normally for over a year prior to this update

I can boot in recovery mode for both the current and previous kernels, but I can't  boot either of them in non-recovery mode

---

### Post by adedr on 2021-02-01
Never figured out the cause. Ended up installing a new os. Frustrating that a simple recommended update can take down my system for no apparent reason.

Thank you to the people who tried to help.

---

