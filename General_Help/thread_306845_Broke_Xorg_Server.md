---
title: "Broke Xorg Server"
date: 2006-11-25
forum: General Help
---

### Post by prophet11 on 2006-11-25
I was trying to setup a dual monitor situation so i pasted a section of code and when i restarted i got a msg saying that there was no monitor..

so i replaced the xorg.conf file with "xorg.conf.orgiginal0" thinking it was going to fix the issue but it didnt.. 

so i did sudo dpkg-reconfigure xserver-org but it said that there was not such server.. so i did sudo apt-get install xserver-org and apt get said it couldnt find it so i did all the upgrades updates dist-upgrade etc still cant find it so im looking for a way to fix this.. my card is a ATI RADEON 9800Pro 128Mb

---

### Post by taurus on 2006-11-25
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by prophet11 on 2006-11-25
ya might have been my typeo ill try it later im going to a wedding now.. do you have AIM> mine is prophet8511 would you please add me im pretty new at linux

---

