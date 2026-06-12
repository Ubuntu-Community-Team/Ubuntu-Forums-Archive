---
title: "Kubuntu kernel panic when using PPPD"
date: 2007-10-22
forum: General Help
---

### Post by pastychomper on 2007-10-22
I had a clean install of Kubuntu 7.04, which was installed in expert mode and connected to the internet using wvdial with an external modem on ttys0.  The system's an Athlon 2200+ with 256MB RAM (32M shared with an on-board Savage4), with Kubuntu installed on a 10GB partition of a 40GB HDD.

After about 2 weeks it started having a kernel panic soon after connecting to the internet (system freezes without warning, caps lock & scroll lock lights flash, the only cure is a hard reset).  It seems to happen randomly, usually within 10 minutes of connecting, occasionally not at all.

I did a complete reinstall, this time using the default graphical install, and connected using KPPP without making any other changes.  Once again, I got a kernel panic within a few minutes of connecting.  I can use the system offline with no trouble.

The system logs show nothing unusual (sometimes nothing at all) in the minutes before the panic.  Memtest86+ reported no errors, and the install DVD also had no errors.

Any suggestions will be much appreciated!

---

### Post by pastychomper on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/156164](https://bugs.launchpad.net/bugs/156164) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've found the same thing happens in Ubuntu 6.06 and filed the above bug report.

---

