---
title: "Laptop shuts down at suspend attempt"
date: 2020-08-09
forum: General Help
---

### Post by quarry96 on 2020-08-09
Hi all
I've recently installed Xubuntu's LTS release Focal Fossa 20.04 on my X220 laptop
When I try to suspend my system, my laptop ends up shutting off. It acts as it usually would when suspending (the power button glowing green and fading out), but I hear my laptop running until it eventually shuts down.

Additionally, when I try to shutdown my machine, the splash screen shows and freezes after a few seconds before shutting off. I don't think it's shutting down as it normally would.

If anyone has any idea about my issue please let me know! Any help would be much appreciated :D

---

### Post by CelticWarrior on 2020-08-10
Welcome.

> [COLOR=#000000]I've recently installed Xubuntu's LTS release Focal Fossa 20.04 on my X220 laptop[/COLOR]

Fine, the OS is identified but the hardware isn't. It suggests some Lenovo Thinkpad X220 of which there are dozens of different models spanning a decade and hundreds of different hardware configurations. Please post detailed hardware information.

And...
Have you installed in UEFI mode? Installing in Legacy/CSM/"BIOS" mode can have the problems you described and more.
Is this a dual-boot? If so, "Fast Startup" in Windows should be disabled.
Other UEFI changes are recommended, namely disabling "Fast Boot" (recommended) and "Secure Boot" (optional but recommended). Please note some firmwares do not explicitly say "Secure Boot" but instead the actual switch is managed by the "OS selection" setting where "Windows" means Secure Boot ON and "Other" means OFF.

---

