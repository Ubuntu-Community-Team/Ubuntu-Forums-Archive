---
title: "Running ubuntu on different from installed hardware."
date: 2021-08-28
forum: General Help
---

### Post by doom52 on 2021-08-28
Hello. I have ubuntu 20.04 and it runs on a hardware that was used during installation well.
But when i try to run it on a different hardware then i have a black screen. I can login to terminal but cannot start desktop.
I have reinstalled nvidia drivers and updated other kernel modules but still no luck
When i type command startx in the terminal i have a message that xserver has been shutdown.
Here is Xorg.0.log - [https://termbin.com/eubcp](https://termbin.com/eubcp)
Is there a way to fix it?

---

### Post by mikewhatever on 2021-08-28
Different hardware could be of a different architecture, for all we know. There are zero details about either machine, so i am not sure what we can do here.

---

### Post by doom52 on 2021-08-28
First has intel processor, second amd ryzen.
first - [https://termbin.com/irsk](https://termbin.com/irsk)
second - [https://termbin.com/8oxp](https://termbin.com/8oxp)

---

### Post by mikewhatever on 2021-08-28
Looks like you've installed Nvidia driver 470.57.02. Is it compatible with the GPUs of both PCs?
Generally, it is not guaranteed that an OS installed on one device will work on another. Sometimes it does, other times it doesn't.

---

### Post by doom52 on 2021-08-28
> **mikewhatever said:**
> Looks like you've installed Nvidia driver 470.57.02. Is it compatible with the GPUs of both PCs?
Generally, it is not guaranteed that an OS installed on one device will work on another. Sometimes it does, other times it doesn't.
Yes, i think it is compatible with both GPUs. And my goal is simple. I only need to make ubuntu run on second configuration.

---

### Post by doom52 on 2021-08-29
i solved this issue by performing these steps.

> 
sudo apt-get remove --purge '^nvidia-.*'
sudo apt-get --purge remove "*cublas*" "cuda*"
sudo apt-get --purge remove "*nvidia*"
sudo rm /etc/X11/xorg.conf
sudo apt autoremove
sudo reboot

 Disable secure boot.
 Reinstalling the driver

 sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
sudo reboot


I found them here - [https://forums.developer.nvidia.com/t/newly-installed-drivers-are-not-found-when-nvidia-smi-is-called/82686](https://forums.developer.nvidia.com/t/newly-installed-drivers-are-not-found-when-nvidia-smi-is-called/82686)

---

