---
title: "Computer keeps freezing, magic Sysreq method not working"
date: 2018-12-25
forum: General Help
---

### Post by jorgeblasio on 2018-12-25
I've been having this issue since installing Ubuntu on this build I made since May 2018. I get random freezes that are not to related to increases in temperature or resource stress. It happens when using Firefox, one time it's happened while the computer screen was dormant. It has never happened while gaming.
The system just freezes. It happened on my first Ubuntu install, Ubuntu Mate 18.04, then in vanilla Ubuntu 18.04 and now on Kubuntu 18.10. There are no logs at all being written and the system does not respond to Alt+Sysrq+REISUB.

How can I find what's wrong with my build?

I'm running Kubuntu 18.10 with Kernel 4.18.0.13
I got a replacement for my processor because it had the Ryzen segfault bug. I'm using an AMD RX 580 with git Mesa from the Oibaf PPA (DRM 3.26. Mesa 19, LLVM 7.01)
I have 16 Gb RAM (3000 DDR4) and I tested it with Memtest and it passed the whole test.

I have no logs being written during freezing, just before the freeze and after normal booting. I'm also missing the Kubuntu logo while booting up although I have an SSD where my system is installed to. /home is on a secondary spinning hard drive. Both keyboard and mouse are USB and connected directly to the motherboard.

Thank you for your help.

---

### Post by tea for one on 2018-12-25
> **jorgeblasio said:**
> There are no logs at all being written and the system does not respond to Alt+Sysrq+REISUB.

Ubuntu does not ship with REISUB fully enabled, therefore I am assuming that it is a similar situation with Kubuntu.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf 
```

Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the ** B** for an **O**

Best wishes

---

### Post by jorgeblasio on 2018-12-25
Thank you, I'll try and hopefiully next time it freezes I can gather debug info.

---

