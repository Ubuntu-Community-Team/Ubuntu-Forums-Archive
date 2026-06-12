---
title: "Problem with &quot;apt&quot; and/or &quot;dkms&quot; blacklisting my amdgpu module."
date: 2024-09-27
forum: General Help
---

### Post by jjvalero on 2024-09-27
I have Ubuntu 24 installed. Every time I install or uninstall some software, even though the task is done correctly it takes too long to complete and I get an error message. The error message is caused by trying to build the "amdgpu" module and an error occurs due to a number of incorrect 
parameters in a "C" function.

Every time it fails it creates the file "/etc/modprobe.d/blacklist-amdgpu.conf" that I have to delete or the graphical environment will not work on the next boot.

I have tried several ways to prevent apt from trying to compile the module. For example, temporarily moving the file "/etc/apt/preferences.d/repo-radeon-pin-600" or deleting the folder "var/lib/dkms/amdgpu" and all its contents. But none of that has worked.

Reinstalling the RTX driver doesn't work as they don't currently have a version for Ubuntu 24. My problems started when I tried to install the driver for version 22 and although I managed to get the card working with some minor issues the problem with "apt" is quite annoying.

---

### Post by deadflowr on 2024-09-27
What card is it?

---

### Post by jjvalero on 2024-09-27
[COLOR=#111111][FONT=-apple-system]Radeon RX 6650 XT[/FONT][/COLOR]

---

### Post by jjvalero on 2024-09-28
SOLVED

Instead of avoiding building the loadable module I found another site with the corresponding version of the module for Ubuntu 24.04. The site is: [https://rocm.docs.amd.com/projects/install-on-linux/en/latest/install/native-install/ubuntu.html](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/install/native-install/ubuntu.html)
Since I already had the module installed, when updating the sources I did a "sudo apt upgrade" and a reboot. Not only this problem has been solved but also several secondary problems I had.

The driver that broke my installation is the one at: [https://www.amd.com/en/resources/support-articles/release-notes/RN-AMDGPU-UNIFIED-LINUX-24-10-3.html](https://www.amd.com/en/resources/support-articles/release-notes/RN-AMDGPU-UNIFIED-LINUX-24-10-3.html)

And finally, I would like to mention that the driver that Ubuntu installed when I changed my old Nvidia card for the Radeon card, although it worked well, caused temperatures of 90 and even 100 degrees. And it forced me to look for the drivers from the manufacturer.

---

