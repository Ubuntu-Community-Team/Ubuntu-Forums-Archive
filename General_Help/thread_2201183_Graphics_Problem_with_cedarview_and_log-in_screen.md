---
title: "Graphics Problem with cedarview and log-in screen"
date: 2014-01-23
forum: General Help
---

### Post by Nolia on 2014-01-23
[SIZE=2][FONT=century gothic][COLOR=#333333]I've recently encountered problems with my netbook when I dabbled with the graphics driver. I recently tried to install the "Cedar Trail in DKMS Format" through Additional Drivers in system settings and got that error in installation that somehow screwed my system up so it can't boot. After numerous hours on google and trying out the suggested fixes, I finally just settled on reinstalling Ubuntu. However now I have these problems:
[/COLOR]
[/FONT][/SIZE]
[LIST=1]
[*][SIZE=2][FONT=century gothic]After re-installing Ubuntu, the log-in screen after waking from suspend is filled with multi-colored vertical lines with a square white box where the mouse pointer should have been. I've encountered this error during my original installation but was able to fix it, although already forgetting how since its been almost a year. I've tried adding nomodeset, acpi_backlight=vendor, removed quiet splash -- everything, but the outcome is the same. I have no choice but to Ctrl +Alt+ F1 and either restart lightdm or to just sudo poweroff or reboot.[/FONT][/SIZE]
[*][SIZE=2][FONT=century gothic]Attempting to try to fix above problem, I've resorted to again installing the graphics driver. I downloaded cedarview-graphics-drivers on synaptic (that goes with cedarview-drm) and the cedarview vaapi driver and now my netbook won't boot. It gets stuck in the boot screen with the Ubuntu logo with the five dots under it and the message that /tmp is not ready, and even if I press S or M to skip or manually restore, nothing happens. Also, cannot continue with the failsafe graphics on recovery, and already ran file system check and broken dependencies. Removing cedartrail does not do anything either. Could there be a way to fix it without having to reinstall Ubuntu again?[/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=century gothic][/FONT][/SIZE]

[SIZE=2][FONT=century gothic][COLOR=#333333]I just want my netbook to go back as it was during the original installation, with the log-in screen fixed. Although now I can't boot unless in recovery mode.[/COLOR]
[COLOR=#333333]
My netbook is an Acer Aspire D270 (Intel Atom N2600, so it's Intel GMA 3600), running on Ubuntu 12.04.04 32-bit.[/COLOR][/FONT][/SIZE]

---

