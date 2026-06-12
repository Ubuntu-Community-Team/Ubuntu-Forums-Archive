---
title: "My screen does not display after booting up"
date: 2008-01-22
forum: General Help
---

### Post by teacup61 on 2008-01-22
I am running gutsy on a multi-boot.  The GRUB comes up and then it starts to do the line entries until it hits a local boot command and then the monitor clicks like it is coming out of hibernate or suspend and just stays as a black screen.  I have rebooted several times and occassionally it will show color on the top one inch of the screen but it is all compressed so you can not read what it is.  I can not get it beyond either situation.  Help, what do I do?

---

### Post by teacup61 on 2008-01-22
I failed to mention that when I boot to Windows XP, it displays correctly, full screen, etc.

---

### Post by silviur on 2008-01-22
Start in recovery mode at boot and log in at the console, then "startx"
If it doesn't work, reboot in recovery mode, and do
```
sudo dpkg-reconfigure xserver-xorg
```
It seems your monitor settings got screwed up.

---

