---
title: "Video Stopped Working After Today's Update"
date: 2015-05-14
forum: General Help
---

### Post by daniell59 on 2015-05-14
Ubuntu 14.04 32

The video on Firefox no longer works after today's update. It still works in Chromium however. I had this problem before, and fixed it by using the terminal. I forgot how I did it.
Any assistance will be appreciated.

---

### Post by daniell59 on 2015-05-14
I was able to solve the problem with the following command sudo apt-get install flashplugin-installer

Afterwards the terminal instructed me to do the following. flashplugin-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
daniel@daniel-N68SA-M2S:~$  I would appreciate it if someone would explain to me how I can follow the instructions in the terminal.

Thanks

---

### Post by SeijiSensei on 2015-05-14
sudo apt-get autoremove

"flashplugin-installer is already the newest version" simply means you already have the latest Flash release.

---

### Post by daniell59 on 2015-05-14
> **SeijiSensei said:**
> sudo apt-get autoremove

"flashplugin-installer is already the newest version" simply means you already have the latest Flash release.

Thanks, is there anything that I should remove?

---

### Post by SeijiSensei on 2015-05-14
> The following packages were automatically installed and are no longer required:
linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.

Autoremove will delete the stale kernel and associated files.  Why do you think you need to remove anything else?

---

