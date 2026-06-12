---
title: "Grub ignoring timeout/hidden  setting after todays update?"
date: 2019-02-01
forum: General Help
---

### Post by Krause on 2019-02-01
Anyone on 18.10 notice after today's update that Grub seems to now show a 20 second wait time regardless of the settings? By default it is completely hidden but after todays updates it shows, and /etc/default/grub still has:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by Impavidus on 2019-02-02
Two days ago I installed an update to grub, which must have been the update that causes your problem. I didn't really pay attention to booting today (or yesterday), but I think I would have noticed a 20 second delay. It appears my delay is still set to 3 seconds.

Do you, by any chance, dual boot two Linux systems? Both Linux systems may have installed the same upgrade to grub and the last system to install the update may have taken over control over grub.

---

### Post by Krause on 2019-02-02
> **Impavidus said:**
> Two days ago I installed an update to grub, which must have been the update that causes your problem. I didn't really pay attention to booting today (or yesterday), but I think I would have noticed a 20 second delay. It appears my delay is still set to 3 seconds.

Do you, by any chance, dual boot two Linux systems? Both Linux systems may have installed the same upgrade to grub and the last system to install the update may have taken over control over grub.

No dual boot, but now im seeing others having this happen after the recent update yesterday in a 24hr google search:

[https://askubuntu.com/questions/1114797/grub-timeout-set-to-30-after-upgrade/1114878](https://askubuntu.com/questions/1114797/grub-timeout-set-to-30-after-upgrade/1114878)
[https://forums.linuxmint.com/viewtopic.php?t=287026](https://forums.linuxmint.com/viewtopic.php?t=287026)

---

