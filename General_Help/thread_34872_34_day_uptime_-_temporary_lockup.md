---
title: "34 day uptime - temporary lockup?"
date: 2005-05-16
forum: General Help
---

### Post by KenMacD on 2005-05-16
Hello,

After running the live cd for about 33-34 days I had the system almost lock up on me. I could change terminals, and display X, and even move the mouse around, but it would not respond to other input. The keyboard on the terminals would do nothing. The CD drive just kept reading for a few seconds, then spinning down, then reading again... etc.

I left it alone to do whatever it was up to, and today (day 35) it appears fine again. I have no idea what caused the instability, as I couldn't run top, but it seems to have finished. I've checked crontabs, atjobs, etc, and can find nothing that would start after 33 days. There were no odd user programs running at the time (X had firefox and xchat opened, but that's about it). Anyone have any idea what may have caused it?

I should also say that I'm very *very* impressed with this live cd from a stability standpoint. I've grabbed gcc, libtools, autoconf, automake, compiled a custom version of wine, installed and run windows applications. All on a machine without a hard drive. It's really going to be a toss up between ubuntu and gentoo for my next install.

One small suggestion for the live cd. Have one of the consoles logged in as root with a nice -10 for cases when you do need to fix something.

Thanks,

Kenny (35 days and counting)

---

### Post by JonahRowley on 2005-05-16
[QUOTE=KenMacD]The CD drive just kept reading for a few seconds, then spinning down, then reading again... etc.[/QUOTE]

I've seen this on machines with dying or picky CDROMs.  The kernel can more or less lock out all reads to the CDROM when one is pending/failing over and over again.  It more or less locks the whole system.  I never found a solution for it, I just rebooted, but that doesn't help your uptime any.

---

