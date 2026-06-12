---
title: "Cannot reach a desktop after updating core X packages"
date: 2014-01-11
forum: General Help
---

### Post by searchfgold6789 on 2014-01-11
The other day, I updated several packages, no more than about 10, I think, including 'xserver-xorg-core'. Now I cannot reach a desktop. When I rebooted, I could not reach a desktop and the screen just froze at the Kubuntu splash screen.

I tried booting to recovery mode and uninstalling and then reinstalling 'fglrx'. Now, when 'fglrx' is installed, I can never boot past the splash screen - typically the monitors enter Power Save Mode immediately after the Kubuntu splash screen. When 'fglrx' is uninstalled, the PC boots until the login loading screen appears (auto login is enabled), but then the monitors enter Power Save Mode.

Anyway, the only thing I know to try is uninstall and reinstall 'fglrx' or 'fglrx-updates' with slightly varying results but I can never get to a desktop. The PC has onboard Radeon APU graphics with nothing attached, and a Radeon HD 5750 with two DVI monitors attached. There is nothing in 'dmesg' that implies anything wrong and the module for 'fglrx' always loads successfully. Anyway I would appreciate your suggestions. Thanks

---

### Post by pbrane on 2014-01-11
Can you boot successfully after removing the fglrx driver, but before re-installing it? You may be able to downgrade xserver-common and xorg-xserver-core. Those are the only two updates that I got that apply to the graphics.

---

### Post by searchfgold6789 on 2014-01-12
Yes ... Or *update* the graphics driver package :P
The one that worked for me was the "Beta" one from [here]("http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx").
Thanks!

---

