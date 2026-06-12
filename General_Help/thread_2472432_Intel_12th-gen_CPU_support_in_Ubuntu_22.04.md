---
title: "Intel 12th-gen CPU support in Ubuntu 22.04?"
date: 2022-02-26
forum: General Help
---

### Post by cbraxton on 2022-02-26
A friend who is sick and tired of Windows and appalled by Windows 11 is having me build him a new computer to run Ubuntu Linux as the primary operating system. (He has been running Linux in a VM for some time in order to get familiar with it.) The plan is to run Ubuntu 22.04 LTS when it is released, probably Ubuntu Mate if that makes a difference.

The issue is whether this new LTS release will have support for Intel's 12th-generation processors. Reading up on it the support has only been added to the newest Linux kernels very recently. So, will the upcoming Ubuntu LTS have 12th-gen support or would it be better to stick with an 11th-generation CPU?

---

### Post by MAFoElffen on 2022-02-27
Well... LOL. If you install with HWE it will be, but... Let me explain.

22.04 will release with general kernel 5.15. The HWE kernel will release with 5.17. Intel iCore 12th Gen patch 'fixes' were applied in Linux kernel 5.17... But some performance enhancing patches were applied to Linux kernel 5.18.

So yes, it will sorta run out of the box, if you install with the HWE (Hardware Enablement Stack). To take advantage of the performance enhancement fixes, you may have to use mainline 5.18. But 5.18 is not released yet... 5.17 is still at 5.17rc5. 

About 2 months until release yet.

---

### Post by cbraxton on 2022-02-27
That's pretty much the way I figured it. I think for the use this guy is going to give it there's nothing all that compelling about the 12th-gen chips, would rather go a generation or two back and just have things work out of the box. He's going to have enough culture shock to deal with as it is. Thanks!

---

### Post by MAFoElffen on 2022-02-27
This is what I did for my own sideline update plan (for a server)... I bought a board that supports Intel iCore 10th Gen. Waiting for the prices of 10th Gen CPU's to get better and gives time for me to try to save for that. 

I'm starting to find that some of my DEV work and testing is getting limited by what I currently have. I can only afford what is "practical."

It usually takes a bit of time for Intel to work things out for a generation series of their CPU's. Especially for their integrated graphics. Even for Windows Users. Everything is already worked out, fairly, for their Gen 10 and Gen 11, but I would hope that prices would start to lower for Gen 10. At least with new releases, people rushing out to chase the latest and greatest then refreshes the used market on them.

The global chip/semi-conductor shortage has complicated things a bit. Look at GPU's...

---

