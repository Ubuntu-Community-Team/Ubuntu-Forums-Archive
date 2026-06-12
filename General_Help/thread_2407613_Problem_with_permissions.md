---
title: "Problem with permissions"
date: 2018-12-06
forum: General Help
---

### Post by web1337 on 2018-12-06
Hi, I have a problem with Opera Browser, I have encrypted veracrypt disk with one partition (not a system disk), I want to put opera download folder on that disk but when I want to select that disk i get permission denied. The path for this disk is /media/veracrypt1. For example qbittorrent download normally on that disk without any warnings. Both are installed from snap.

---

### Post by TheFu on 2018-12-06
snaps have added security in that they don't allow writes to just anywhere on the file system.  They are little sandboxes. In theory, there should be  a way to control which directories are allowed to be written, but I've avoided snaps completely.  [https://forum.snapcraft.io/t/custom-disk-location-for-certain-snaps/3022](https://forum.snapcraft.io/t/custom-disk-location-for-certain-snaps/3022) says it isn't likely.

I use a different sandbox tool - firejail - which allowed different profiles to be used at runtime to determine which areas are allowed to be read-only and read-write.
/etc/firejail/ has about 50 example profiles which can be used to make one to fit your needs.  Of course, any program that ran under a firejail sandbox couldn't be a snap install.

BTW, opera is owned by a Chinese consortium of companies after the Norwegian group sold it.  [https://techcrunch.com/2016/02/25/opera-ceo-sale-to-chinese-consortium-wasnt-our-decision/](https://techcrunch.com/2016/02/25/opera-ceo-sale-to-chinese-consortium-wasnt-our-decision/)

---

### Post by l33ch on 2018-12-06
> **TheFu said:**
> snaps have added security in that they don't allow writes to just anywhere on the file system.  They are little sandboxes. In theory, there should be  a way to control which directories are allowed to be written, but I've avoided snaps completely.  [https://forum.snapcraft.io/t/custom-disk-location-for-certain-snaps/3022](https://forum.snapcraft.io/t/custom-disk-location-for-certain-snaps/3022) says it isn't likely.

I use a different sandbox tool - firejail - which allowed different profiles to be used at runtime to determine which areas are allowed to be read-only and read-write.
/etc/firejail/ has about 50 example profiles which can be used to make one to fit your needs.  Of course, any program that ran under a firejail sandbox couldn't be a snap install.

BTW, opera is owned by a Chinese consortium of companies after the Norwegian group sold it.  [https://techcrunch.com/2016/02/25/opera-ceo-sale-to-chinese-consortium-wasnt-our-decision/](https://techcrunch.com/2016/02/25/opera-ceo-sale-to-chinese-consortium-wasnt-our-decision/)

crap.....and I liked Opera too... I was looking into how to sandbox/jail various flash-enabled firefox installations I have. You mentioned Firejail...I'll have to look into that.

---

