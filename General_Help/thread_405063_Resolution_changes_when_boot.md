---
title: "Resolution changes when boot"
date: 2007-04-09
forum: General Help
---

### Post by Petester on 2007-04-09
I have my nvidia drivers installed and set to 1440x900 (19'' Widescreen, big screen i know XD)  but then each reboot (or boot) it returns to 1024x768

I have already "save Xorg Config files" Or similar in the nvidia driver... how should i solve it?

---

### Post by chewearn on 2007-04-09
Instead of running Nvidia-Settings from the panel menu, run it from terminal with sudo:
```
sudo nvidia-settings
```That way, it will have the permission to overwrite xorg.conf

---

### Post by Petester on 2007-04-09
Thanks a lot. I will tell you what happend in my next boot

---

