---
title: "boot trouble ununtu 16.04"
date: 2020-11-12
forum: General Help
---

### Post by Gingalone on 2020-11-12
After years of good service, a few days ago my Ubuntu 16.04 Samsung 5 laptop did not boot: it stopped (and continues to do that ever since) displaying the name of the hard disk (SATA HDD:: etc.) and when I do a return the system goes instantaneously back there; under the App Menu option I can enter in the BIOS, but there everything looks OK.
Quite obviously it seems there is some problem with the hard disk: what can I try to do in order to understand the problem and try to solve it? Any possibility to check/mend the disk?
(I  have a USB flash drive with Ubuntu 16.04, could that be useful?)
Thank you for any help.

---

### Post by tea for one on 2020-11-12
Have you tried to boot your USB Flash Drive with Ubuntu 16.04?

If it boots OK, then back up your data before anything else - this is essential.

Then, try and boot your PC via Grub > Advanced Options > Recovery mode

Any error messages?

Or possibly boot into a different kernel?

---

### Post by Gingalone on 2020-11-15
Thank you tea for one, I solved the problem just changing the boot mode to CSM in BIOS (instead of UEFI), now my laptop boots regularly from its HD. That's strange because I had never changed the boot mode before... Anyway, following your advice, I did a complete backup of the disk!

---

