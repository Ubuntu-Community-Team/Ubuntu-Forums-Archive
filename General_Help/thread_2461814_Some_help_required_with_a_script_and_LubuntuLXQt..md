---
title: "Some help required with a script and Lubuntu/LXQt."
date: 2021-05-07
forum: General Help
---

### Post by ayesc0tty89 on 2021-05-07
I'm using 21.04 and a Raspberry Pi 4B 4GB. the script installs stuff I want, enables them and copies over configs.
But; there's a problem! It copies over: lxqt-config-appearance.conf & lxqt.conf but every-time I logout and/or reboot. LXQt falls back to defaults and I have to select openbox as the manager! this happens every-time!

What can I do to solve this?

The script in question is; [https://paste.ubuntu.com/p/cmpNcv4Dvy/](https://paste.ubuntu.com/p/cmpNcv4Dvy/)

Yes, it does a lot but it works so it's okay!

Thanks in advance for your help!

---

### Post by dragonfly41 on 2021-05-07
I don't pretend to understand the script .. but isn't it just a matter of adding some extra logic to these lines

115 mv lxqt.conf /home/pi/.config/lxqt/

117 mv lxqt-config-appearance.conf /home/pi/.config/lxqt/

That is, only apply these mv commands if /home/pi/.config/lxqt/ is empty? Or based on some conditional flag?

---

### Post by ayesc0tty89 on 2021-05-07
Thanks for the reply!
Weird thing is, I just rebooted and booted back up without my external plugged in and it's fine, don't have to select openbox. :)

---

