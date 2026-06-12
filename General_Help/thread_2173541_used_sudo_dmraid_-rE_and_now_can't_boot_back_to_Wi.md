---
title: "used sudo dmraid -rE and now can't boot back to Windows partition"
date: 2013-09-10
forum: General Help
---

### Post by baris2 on 2013-09-10
Hello, in an attempt to dual-boot Windows 7 and Ubuntu 13.04, I've made a grave error. When the installation was not showing any disk partitions to install to, a simple sugestion of "sudo dmraid -rE" fixed it. However now I cannot acess either Linux nor Windows 7, getting only a "DISK BOOT ERROR" in response. I've tried installing grub and the bootloader, and I've already completely cleared the Linux parition in an attempt to get everything working to no avail. I am currently posting this from the Live DVD.

Please answer quickly, a tangible part of my life and soul is on the line here!

---

### Post by baris2 on 2013-09-10
Solved. Turns out the DMRAID command had nothing to do with my problem, grub just freaked out and wouldn't let my PC start. Uninstalled Ubuntu and restored the bootloader from my Win7 disk (thanks to this thread [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)) and everything is good to go.

---

