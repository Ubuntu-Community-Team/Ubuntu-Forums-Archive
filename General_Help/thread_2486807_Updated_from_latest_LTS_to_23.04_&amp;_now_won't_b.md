---
title: "Updated from latest LTS to 23.04 &amp; now won't boot"
date: 2023-05-11
forum: General Help
---

### Post by the.real.frank.paganini on 2023-05-11
I updated to 23.04 and rebooted. Everything worked fine for a week. Then I installed my latest updates and now it won't boot beyond this message: [https://ibb.co/Q8XVkBB](https://ibb.co/Q8XVkBB)

Someone on Reddit suggested reinstalling snap so I did but got this message:
[https://ibb.co/xG8FTCL](https://ibb.co/xG8FTCL)

On reboot I get the same error as the first image I shared so obviously reinstalling snap didn't fix it. 

Any tips?

I'm running kubuntu 23.04

---

### Post by the.real.frank.paganini on 2023-05-11
I removed the canonical livepatch snap and the original error message went away and I'm not seeing any new errors but it's still hanging in the same point of the boot process.

---

### Post by the.real.frank.paganini on 2023-05-11
Won't boot into the 6.2.0-20 generic version of the kernel or 5.19.0-41 generic . Both options hang at the same point in the boot process. Recovery mode will work but that's about it. 

What gives?

---

### Post by the.real.frank.paganini on 2023-05-11
Fixed it. 

While looking around in recovery mode I noticed my graphics driver was missing. Why?  I don't know because it was installed and working fine when I last updated my computer but apparently somewhere between the update and the next boot the driver was removed.

Reinstalling the graphics driver fixed the problem completely.

---

