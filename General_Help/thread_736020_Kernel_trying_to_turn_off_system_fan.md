---
title: "Kernel trying to turn off system fan???"
date: 2008-03-26
forum: General Help
---

### Post by NeatO7364 on 2008-03-26
Note: I've already posted this once in Hardware & Laptops but am really anxious to find help to this problem as soon as I can.

Hi all,

I have been using Ubuntu for almost 6 months now on an Intel Celeron computer (about 4 yrs old) and it has served as a rock-solid server. However, I recently began having a strange error in which the kernel appears to be trying to turn off the computer's one internal fan (it's in a micro-ATX enclosure, but yeah, still probably not the best idea when it comes to heat dissipation). The biggest problem is that the kernel is trying to do this multiple times per second and I'm using logcheck to keep an eye on my system logs, so I get emails that are approximately 70,000 lines long (not an exaggeration!). Furthermore, I believe that the kernel is using up resources like crazy, and the system locks up for about 10 seconds at a time while this is happening.

Here is a VERY brief snippet of what I'm getting:

Mar 26 00:26:00 axs kernel: [13246.552593] ACPI: Transitioning device [FAN1] to D3
Mar 26 00:26:00 axs kernel: [13246.552603] ACPI: Transitioning device [FAN1] to D3
Mar 26 00:26:00 axs kernel: [13246.552607] ACPI: Unable to turn cooling device [e6aa82a0] 'off'

Why is the kernel trying to turn the CPU fan completely (D3!) off? I had read elsewhere that a kernel update fixed the problem, so I went ahead and did a complete system upgrade to the latest stable Ubuntu 7.10 but I'm still getting this crazy error. Would moving the system to a more modern motherboard and possibly larger case (with more fans) help?

Thanks in advance for any and all advice!

---

### Post by babyfoxx on 2008-03-26
I had this same problem, and I just unplugged the fans from the sensor power plug in, and plugged them in straight (always running). If that makes any sense. 

I'd rather have fans running than a over-heated PC.

---

### Post by drbob07 on 2008-03-26
Are you positive FAN1 is your CPU fan, and not a rear exhaust fan?

I've had 3 laptops and all of them, even the ones running Windows, turn their rear exhaust fans off at one point or another throughout the day. (Although I thought this was controlled directly by the hardware, not the kernel, :P)

---

### Post by NeatO7364 on 2008-03-26
I am positive it's the CPU fan... in this micro-ATX enclosure, it's the only system fan in there... I checked twice to be sure.  I'm thinking that perhaps I will unplug the fan from the motherboard sensor and directly into its power outlet.

---

