---
title: "PCManFM/GVFS cannot mount ext4 USB drives"
date: 2013-01-16
forum: General Help
---

### Post by PeterTaps on 2013-01-16
Folks,

Environment: Ubuntu 12.04 + Openbox

I am running PCManFM in the background with "--desktop" option. The idea is any new USB drive that is connected gets mounted automatically.

With this, I am able to mount any external USB drive that is formatted as FAT, exFAT and NTFS. However, if I have a USB drive that is formatted as ext4, PCManFM is not able to mount it.

Upon further investigation, it appears PCManFM can mount ext4 drives only if it is run with "sudo" privileges. 

I am wondering why is this the case. Is it possible to mount external ext4 USB drives without sudo privileges?

Thank you in advance for your help.

Regards,
Peter

---

