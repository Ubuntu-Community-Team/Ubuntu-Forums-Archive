---
title: "Nvidia settings not working + games not using discrete gpu"
date: 2019-07-22
forum: General Help
---

### Post by 5348097045-swh on 2019-07-22
Tried reinstalling Ubuntu without the GPU and then inserting it and installing the drivers directly from Nvidia didn't help. GPU is being detected just not used. When run from terminal:
(nvidia-settings:3054): GLib-GObject-CRITICAL **: 16:28:08.378: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 16:28:08.381: PRIME: No offloading required. Abort
** Message: 16:28:08.381: PRIME: is it supported? no

lspci |grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation Device 2182 (rev a1)
07:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c6)

graphics card is a 2060ti.

---

### Post by mastablasta on 2019-07-23
what happens if you disable radeon? e.g. blacklisting the module. it could be it is interfeering. i knwo intel & nvidia should work,not sure how well radeon and nvidia would mix since they are rival chips.

---

### Post by 5348097045-swh on 2019-07-23
Not really sure how to disable radeon the main issue is I can't just disable it in BIOS as NVIDIA had the great idea of using DP for all but one connector and I have two monitors.

---

### Post by oldfred on 2019-07-23
Best not to install drivers direct from nVidia. You have to reinstall (update initramfs) with every kernel update. If you use Ubuntu ppa, then it is all automatic and you still have newer driver.

You must purge any installed driver before attempting to install a newer or different driver. New driver does not uninstall old and then creates conflicts causing more issues.

To see what is installed:
       dkms status
lsmod | grep nvidia
nvidia-smi 

      
 Uninstall the .run nVidia driver.
[https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)
Install nVidia
[https://askubuntu.com/questions/1026179/how-to-install-a-gtx-1060](https://askubuntu.com/questions/1026179/how-to-install-a-gtx-1060) & 
[https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers) 
    
       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)

---

### Post by mastablasta on 2019-07-24
> **5348097045-swh said:**
> Not really sure how to disable radeon the main issue is I can't just disable it in BIOS as NVIDIA had the great idea of using DP for all but one connector and I have two monitors.

for example: [https://askubuntu.com/questions/938658/how-to-blacklist-radeon-module](https://askubuntu.com/questions/938658/how-to-blacklist-radeon-module)
or for AMDGPU: [https://askubuntu.com/questions/1080217/how-to-blacklist-amdgpu-driver](https://askubuntu.com/questions/1080217/how-to-blacklist-amdgpu-driver)

not sure if it's radeon or AMDGPU in your case. i would suggest a bit more research into this. in any case this should still allow you to boot into text mode or repair mode to at least get the GPU back if it fails. i wouldn't disable it in BIOS.

also what oldfred said. use ubuntu nvidia PPA for drivers. additional drivers application in ubuntu should also work.

---

### Post by him610 on 2019-07-24
FWIW, I have an Asus MB with AMD integrated GPU to which I installed a Nvidia GTX750. In the BIOS/UEFI settings the GPU priority can be set that permits the peripheral GFX drivers to be loaded first. 
Never experienced an issue with this method.

---

### Post by 5348097045-swh on 2019-07-24
Is there any solution to Nvidia settings not working in the lastest kubuntu?

---

