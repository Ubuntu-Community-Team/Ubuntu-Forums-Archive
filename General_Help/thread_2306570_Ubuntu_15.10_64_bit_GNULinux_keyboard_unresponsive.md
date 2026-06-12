---
title: "Ubuntu 15.10 64 bit GNU/Linux: keyboard unresponsive at plymouth screen for password!"
date: 2015-12-16
forum: General Help
---

### Post by Welly Wu on 2015-12-16
I got my new 2015 Sager NP8657 [Clevo P650-RE3] notebook PC and I successfully installed Ubuntu 15.10 64 bit GNU/Linux on it along with my favorite software products, packages, libraries, and dependencies. I enabled full-disk encryption and the plymouth screen shows the prompt for me to enter my master password to unlock my notebook PC, but my keyboard is not working so I can't enter my password. I have to press CTRL + ALT + DEL and restart the notebook PC until I see a blank purple screen and then I can type in my master password to unlock my notebook PC to boot up Ubuntu 15.10 64 bit GNU/Linux. I researched this technical issue and it is well known beginning from Ubuntu 14.10 64 bit GNU/Linux until the current version. I was wondering if anyone is experiencing the same technical issues and if there is a better solution available other than my workaround? Please reply if you can help me. Thank you.

---

### Post by Welly Wu on 2015-12-17
I checked my initramfs-tools package version and it is the latest version. I modified my /etc/initramfs-tools/modules to include i2c_hid, hid_generic, usbhid and I did sudo update-initramfs -u. I rebooted and it still does not work. I can't enter my password at the Plymouth busy box screen. I have to restart a second time for the GRUB2 bootloader to appear and select Ubuntu where I have to wait for a blank purple screen to enter my master password to unlock my notebook PC. This is as much progress as I have made which is to say that I am stuck at square one. Can anyone help?

---

### Post by Welly Wu on 2015-12-18
It's a known bug with systemd in Ubuntu 15.04 and 15.10 that affects encrypted swap partitions. It seems that I am going to have to wait until Ubuntu 16.04 64 bit LTS GNU/Linux for this problem to get solved. In the meantime, I will have to restart my notebook PC twice in order to load the GRUB2 bootloader and enter my master password at the blank purple screen to boot up Ubuntu 15.10 64 bit GNU/Linux. There is not much I can do until Canonical, Ltd. fixes this technical issue next year. I'll keep this thread updated until a patch is released.

---

### Post by slickymaster on 2015-12-18
@Welly Wu
You tagged this thread as Lubuntu but your posts indicated that you have Ubuntu installed instead. It's probably for the best that you correct it to the right tag.

---

### Post by Welly Wu on 2015-12-18
Thanks. I updated the tag.

---

