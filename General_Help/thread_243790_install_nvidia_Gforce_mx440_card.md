---
title: "install nvidia Gforce mx440 card"
date: 2006-08-25
forum: General Help
---

### Post by Tucatts on 2006-08-25
I need some instructions on how to install the drivers for this nvidia card, Gforce mx440. I just installed Goole earth which installed great but it says I don't have drivers for my nvidia card. I just went to terminal and put in "
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable" Ran the command and told me that the current configuration was up to date. However, still don't think I have the drivers. I dual boot this machine (2g celeron,512 memory) and google earth works fine on my XP boot so I know that this card will work even though it is an old one. ANyway need to install the drivers.
Thanks,
Tucatts

---

### Post by steve.horsley on 2006-08-25
I seem to remember reading somewhere that the mx440 had been relegated to some kind of legacy driver. There is a nvidia-glx-legacy driver in the repos that you could try.

---

### Post by rgsproductions on 2006-08-26
I am running a nvidia geforce4 mx420.  I had the legacy drivers and found out it is not a legacy card, I installed the proper ones.  I used these posts  "NVIDIA LIST of videocards supported through LEGACY DRIVER" or 
'the binary how to /nvidia documentation".  Both post helped me get my card running. [http://www.ubuntuforums.org/showthread.php?t=233241](http://www.ubuntuforums.org/showthread.php?t=233241)

I ran google earth on both drivers just fine.  Did you also install the  linux-restricted-modules for your kernel?
hope this helps

---

### Post by jISh on 2006-08-26
I'm using the same card with regular nvidia-glx drivers.
Open your xorg.conf (gksudo gedit /etc/X11/xorg.conf) and change "nv" to "nvidia" under the device section, if it isn't already changed. Then reboot.

If you see the nVidia logo before the login screen, it works properly.

---

