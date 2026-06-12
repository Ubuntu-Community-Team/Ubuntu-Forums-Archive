---
title: "Only have access to tty terminals after deleting nvidia (no access to GRUB or GUI)"
date: 2019-10-25
forum: General Help
---

### Post by alex5652 on 2019-10-25
Hello, my configuration is Ubuntu x86-64 18.04.3 with a 4.15.0-66 kernel and a GeForce RTX 2060 SUPER graphic card.

By following a tutorial ([https://zhuanlan.zhihu.com/p/49166211](https://zhuanlan.zhihu.com/p/49166211)) to reinstall cuda and tensorflow, I entered the following command lines (step 6 in tutorial)


sudo apt-get purge nvidia*
sudo apt-get autoremove
sudo apt-get autoclean
sudo rm -rf /usr/local/cuda*
sudo apt install dracut-core
sudo gedit /etc/modprobe.d/blacklist.conf
append one line to the file:
          blacklist nouveau
sudo update-initramfs  -u


After rebooting, my machine is now stuck on a screen with /dev/nvme0n1p2: clean xxx/xxx files, xxx/xxx blocks. I can access to tty2-tty6 terminals using Ctrl-Alt-FX, then login and access to my files but only on the terminal with no graphic interface at all. If I reboot I cannot start the Grub recovery mode, even after changing the GRUB_TIMEOUT=10 and GRUB_TIMEOUT_STYLE=menu.

I also tried reinstalling all my drivers but nothing worked. We could access and display the correct information with nvidia-smi but still no GUI. Any reboot would just bring me back to that /dev/nvme0n1p2... screen.

I know that the machine was configured from scratch (maybe Linux From Scratch) and I guess that I removed some crucial thing with the drivers.

Do you have any idea of what to try to get my GUI to work again?

---

