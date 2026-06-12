---
title: "[SOLVED] How to remove OSS?"
date: 2007-12-25
forum: General Help
---

### Post by TidusBlade on 2007-12-25
Well I screwed up my sound, and now I wanna remove OSS, to use ALSA and use alsa-oss to use OSS from ALSA. So is there any safe way to remove OSS and get back ALSA? 
Any help is welcomed, Thanks!

---

### Post by tgilber1 on 2007-12-25
> **TidusBlade said:**
> Well I screwed up my sound, and now I wanna remove OSS, to use ALSA and use alsa-oss to use OSS from ALSA. So is there any safe way to remove OSS and get back ALSA? 
Any help is welcomed, Thanks!

I have everything related to OSS uninstalled, and the sound works fine.  

1.  dpkg -l "*oss*" # to get list of oss packages installed
2.  sudo apt-get remove <oss packages>  #populate list of oss packages you want to remove
3.  sudo apt-get install alsa-base alsa-oss

---

### Post by TidusBlade on 2007-12-25
Thanks! Got ALSA working perfectly now :)

---

