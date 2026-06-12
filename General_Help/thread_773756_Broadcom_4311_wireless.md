---
title: "Broadcom 4311 wireless"
date: 2008-04-29
forum: General Help
---

### Post by xecure on 2008-04-29
hi, after freshly installing 8.04 i saw that my wireless wasn't working so I went over to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc") to try and get my wireless to work. Fortunately it was detecting wireless broadcasts (don't know if it works because I can never connect to wireless from my dorm anyways, they are just here) 

But my problem is that not that it detects wireless connections it cannot detect any wired connection.

I ran ```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local

``` in terminal hoping I wouldnt have to set up the driver everytime I rebooted, but now that I have done that my wired connection cannot be detected

---

### Post by xecure on 2008-04-30
bump..

---

### Post by frodon on 2008-04-30
Duplicate thread closed.

User willing to help please answer in the following thread :
[http://ubuntuforums.org/showthread.php?t=773774](http://ubuntuforums.org/showthread.php?t=773774)

---

