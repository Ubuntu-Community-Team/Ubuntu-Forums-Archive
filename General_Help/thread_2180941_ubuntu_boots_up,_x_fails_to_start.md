---
title: "ubuntu boots up, x fails to start"
date: 2013-10-15
forum: General Help
---

### Post by baabsaget on 2013-10-15
I have run ubuntu on my macbook pro 9, 2 for almost a year now. I have to use proprietary driver, so plymouth doesn't work and the screen is very ugly on bootup. I decided that instead of watching the broken plymouth splash screen on boot, I would rather just boot verbosely every time. I opened /etc/default/grub and got rid of quiet splash, updated grub, and rebooted. When the login screen would normally appear, I got a completely black screen. No cursor, nothing. I booted in recovery mode and added quiet splash back to /etc/default/grub, but the black screen persisted. I again rebooted into recovery mode and tried failsafeX, but it came up with an error saying no screens detected. I have no idea why this is happening, please help.

---

