---
title: "Ubuntu 22.04 LTS Will not boot Dell 3650 and Nvidia RTX A2000 after current update"
date: 2023-08-15
forum: General Help
---

### Post by foxsquirrel on 2023-08-15
This just happened on our second machine. First machine we assumed the RTX A2000 crapped out. That is not the issue, just did an update on another 3650 with A2000 card and it broke the second machine.
Emergency fix is to pull the video monitors off the A2000 and plug into the native DP connectors on the Dell box.

Not sure what the exact cause is at this moment.

---

### Post by MAFoElffen on 2023-08-16
So starting out from the Grub2 boot menu replacing "quiet splash" with "-- 3 nvidia.nomodeset=0", you were not able to get to a console only login where you could reinstall the nVidia drivers?

After using nVidia with Unix and Linux since 2005, is is common after a kernel update to have to reinstall the driver, where it re-compiles the binary with the new kernel. After nvidia-dkms came into play, that took care of a lot of that, but it still happens.

Which driver were you using? 535.98?

---

### Post by foxsquirrel on 2023-08-17
> **MAFoElffen said:**
> So starting out from the Grub2 boot menu replacing "quiet splash" with "-- 3 nvidia.nomodeset=0", you were not able to get to a console only login where you could reinstall the nVidia drivers?


Does not go that far, stops after the memory block line in the upper left of the screen.

If it had a debug port I could see exactly where it is stopping.

---

### Post by oldfred on 2023-08-17
Recovery mode in grub uses nomodeset, without the extra parameters. That often boots to recovery mode menu.

I always change quit splash to noplymouth which then shows each of the lines added to the log files. It used to be slow enough you could follow, but now with SSD, it is very fast.

---

