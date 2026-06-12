---
title: "Freezing problem with Ubuntu 12.04 LTS 64-bit Nvidia-319 drivers"
date: 2014-01-11
forum: General Help
---

### Post by mpacey13 on 2014-01-11
Hello Ubuntu Community!

I'm currently facing a problem in Ubuntu 12.04 LTS whenever I activate the Nvidia-319 proprietary driver (Stable Release and Post-Release Updates) I start freezing at random intervals, sometimes the freezes occur many times, sometimes hardly any, however it is starting to become a bother constantly ctrl + alt + f1'ing to unfreeze myself! 

Any assistance in this matter would be greatly appreciated, I know you guys will probably want some logs, so just let me know what ones you want and i'll post em for you!

Thanks guys!
mpacey :D

---

### Post by efflandt on 2014-01-12
After you Ctrl+Alt+F1 have you checked the tail end of **dmesg** or any logs in **/var/log/**, like **Xorg.0.log**, **syslog**, etc. Do you have Nvidia graphics only, or combo Intel/Nvidia graphics (not sure if newer desktops have that or just newer laptops)?

I am using **nvidia-experimental-310** transitional package (since that is what Steam recommended a year ago when I got into that), which is currently nvidia 319.32 in 12.04, and this is what "sudo lspci -v" shows for modules:
Kernel driver in use: nvidia
Kernel modules: nvidia_319_updates, nouveau, nvidiafb

Did you use **nomodeset** kernel boot parameter during install, which then uses that automatically after install? If that parameter does not show up on all Linux menu entries on **linux** lines in **/boot/grub/grub.cfg**, you may need to add that to the following line in **/etc/default/grub** and then run **sudo update-grub** and reboot.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

That allows separate video modules to be used instead of only what is built into the kernel (kernel mode setting).

The only peculiar nvidia thing that happened when I think a Galaxie video card (Nvidia GT 430) itself was failing (after its 1 yr warranty expired). Win7 started saying "video driver stopped responding, recovered", but in Linux occasionally keyboard and mouse buttons would stop responding (but mouse cursor could usually still move). Eventually it got to the point that I got kernel boot messages that nvidia hardware was not responding or in some cases scrambled video pattern. I replaced the card with EVGA GTX 550 Ti (3 yr warranty) some years ago, and no video problems since.

---

### Post by mpacey13 on 2014-01-27
Sorry for an incredibly late reply.

I have sorted my problem now, I added the x-swat PPA and it updated my 319 drivers and that has sorted the problem alone. Strange that the official repositories would provide me with buggy drivers.

Thanks for your help!

---

