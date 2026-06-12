---
title: "Ubuntu not booting on Dell Inspiron"
date: 2021-05-19
forum: General Help
---

### Post by steve0691 on 2021-05-19
Hi, I have a newish Inspiron which came preloaded with Ubuntu 18.04 and has worked fine for over a year. Recently it has started booting to the Grub command line instead of Ubuntu. This happens most of the time but sometimes it boots OK. Any help would be appreciated.
Thanks, 
Stephen.

---

### Post by oldfred on 2021-05-19
Does this show anything. But it is after grub has loaded.
sudo grep -E -i "error|warning" /var/log/dmesg 

Do you have good backups, could be sign of drive issues.

This will show boot configuration, but if it works sometimes, it may not show anything.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by steve0691 on 2021-05-19
Hi, thanks for the quick response but what you are saying is beyond my knowledge I'm afraid. Thanks.

---

