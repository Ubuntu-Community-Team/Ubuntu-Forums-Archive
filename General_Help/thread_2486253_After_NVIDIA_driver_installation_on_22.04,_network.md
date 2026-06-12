---
title: "After NVIDIA driver installation on 22.04, network, bluetotth, touchpad disappeared."
date: 2023-04-24
forum: General Help
---

### Post by yurad on 2023-04-24
Several days ago I installed the NVIDIA driver 530  via Software and  Updates and rebooted. After the reboot, X server didn't start. I got a black screen instead  of the GUI login screen. In the terminal, I changed prime-select to "intel" and rebooted again. X  started and I was able to login to GNOME. However, I completely lost  network, WiFi, Bluetooth, touchpad, and sound.  pulsaudio is running, however, there is no sound. I uninstalled NVIDIA and  rebooted again. Then I found that Wayland had  also disappeared from the  login options.  Network restart and puslaudio restart have no effect.  Also, I can no longer hibernate. "systemctl hibernate" just logged me out from the Gnome session. 
What could be the the problem? Is it kernel corruption?

---

### Post by watchpocket on 2023-04-25
> **yurad said:**
> Several days ago I installed the NVIDIA driver 530  via Software and  Updates and rebooted. After the reboot, X server didn't start. [ . . . ]

Without  knowing anything about your system, I would ***sudo apt purge*** Nvidia driver 530 and re-install whichever one you had previously.  I'm using driver 470 and won't "upgrade" until I know what I'm getting with it. 525 and 530 from what I've been seeing are not primetime-ready drivers. (Not sure about 510 and 515 but I wouldn't trust them either until I was sure.) 

If all the other stuff is still missing, I'd just re-install it once you know you're driver isn't giving you problems.

---

### Post by Autodave on 2023-04-26
525 is good now.....been using it on 3 different machines with no problem.  However, I saw that 530 was available, but when I clicked on it to install, there was a huge list of things that were going to be changed.  Instead, I changed my mind and did not install it.

---

### Post by yurad on 2023-04-26
First of all, thank you for the replies! I will add more information. 
I had NVIDIA 525 installed. Then, GNOME and KDE were crashing every 2-3 days. I had NVIDIA on-demand setting. It was possible to change prime-select to intel, but then I didn't see any advantage of NVIDIA driver. So, I was thinking to switch again to nouveau. However, before switching, I found NVIDIA 530 and decided to try it first. My bad. 

To install again NVIDIA 525, I believe better to have the network working. I am not sure if I can simply download 525 and install it offline. As I said above, when I boot with my latest kernel 5.15.0-71-generic I don't see network, wifi, bluetooth, sound, and touchpad, Also I am unable to suspend/hibernate. 

Then. I tried to boot with old kernels. Right now I have booted with 5.15.0-67-generic . Everything looks working with old kernels: network, wifi, bluetooth, sound and touchpad, except I still cannot suspend. But, nouveau gives me an error:   
kernel: nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 6013d4 [ PRIVRING ] . 
Probably, nouveau still doesn't work with my card, GeForce 940MX. Although formally it should work. I see this card in the supported list: 
NV118 (GM108) GeForce 830M, 840M, 930M, 940M[X]. 
Maybe 5.15.0-70 has a newer nouveau, but I couldn't figure it out. 

What should I do to fix kernel 5.15.0-71-generic?  Try to install NVIDIA 525 offline after booting with 5.15.0-71? Is there another safe way to recover 5.15.0-71 offline? 
Also, what could be the reason that suspend/hibernation stopped working?

(BTW, I was wrong saying that Wayland had disappeared from the login options when I boot with the latest 5.15.0-71. In fact, Xorg had disappeared. With 5.15.0-71 I can use only Wayland. But, when I boot with old kernels,  both Xorg and Wayland are available.)

---

### Post by tomdixon on 2023-04-30
With me the 530 installed but I do not get any normal speed with that. It is like Nouveau driver. All flavors of 525 seem to work well under load and gaming too.

---

### Post by yurad on 2023-05-01
I fixed my latest kernel, 5.15.0-71-generic .
I just needed to reinstall modules-extra
sudo apt install --reinstall linux-modules-extra-5.15.0-71-generic 

All devices work now. 
Still, I cannot  suspend/hibernate. But, most probably it is a nouveau problem, which I hope to resolve soon.

---

