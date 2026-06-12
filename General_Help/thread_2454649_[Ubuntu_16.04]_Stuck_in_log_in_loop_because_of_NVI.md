---
title: "[Ubuntu 16.04] Stuck in log in loop because of NVIDIA Driver ver. 430"
date: 2020-12-03
forum: General Help
---

### Post by dulipat on 2020-12-03
[COLOR=#333333][FONT=DIN-Web-Pro]Hello,[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]I installed the NVIDIA Driver ver. 430 to my Ubuntu 16.04, but then I got stuck in the log in loop (i.e, When I try to log in to Ubuntu after starting up, I get taken right back to the same login screen, and the process repeats indefinitely). This problem can be solved ONLY by removing the driver. So, my question is, what is the recommended NVIDA Driver for Ubuntu 16.04? I have a GeForce RTX 2070. One additional info: I installed the driver using the apt-get command because the driver is not listed in the “Software Updater”.
I appreciate any help. Thanks[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-12-03
Welcome.

Ubuntu 16.04 has only a few months left of support. Please do your backups and install a fresh Ubuntu 20.04 making sure that the option to install drivers, codecs, etc. is ticked. This will automatically install the recommended driver for your card, unlike what happened with your current release.

---

