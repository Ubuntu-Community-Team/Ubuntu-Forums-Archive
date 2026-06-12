---
title: "Create bootable / installable Live from installed system?"
date: 2022-06-16
forum: General Help
---

### Post by kawazu on 2022-06-16
Alls;
not sure where to place this, hope this isn't all too wrong: Coming from / fancying MXLinux at times, I really do appreciate their snapshot tool where it's dead-simple to create a bootable, installable variant of whichever system configuration is currently running. This is pretty neat to, in example, prepare an installation in a virtual machine to a point where it's "good" and then roll it out to a a live stick, a laptop or another physical device.
Question's: How to do something similar with Ubuntu? Are there any current means or best practises on how to do that? All the tutorials I stumbled across rely on tools and code that seems to have been abandoned on sourceforge or github ages ago...
Any ideas or pointers greatly appreciated. :)
Thanks and best,
Kristian

---

### Post by yancek on 2022-06-16
The first software of this kind I was aware of was remastersys.  Unfortunately, that has been abandoned for years as it was a one man project and he could not maintain it any longer.  There were several replacements and the last 'current' one I am aware of is Systemback, see the link below.  I noticed on this site the last date was over 2 years ago so it may no longer be developed.

[https://www.alibabacloud.com/blog/a-quick-guide-to-using-systemback-for-ubuntu-backup_595818](https://www.alibabacloud.com/blog/a-quick-guide-to-using-systemback-for-ubuntu-backup_595818)

I'm no longer up to date on this kind of software so am not aware of anything similar.  If the tool is available on MXLinux and you need it, you may need to switch back.  PCLinuxOS has similar software but it only works for PCLinuxOS.  Good luck.

---

### Post by HermanAB on 2022-06-16
The way to autoinstall and roll a system out to one or thousands of machines, is with Kickstart (Redhat) or Preseed (Debian). https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html?m=1

---

### Post by web-user on 2022-06-18
You can use dd to copy the installation to flash drive like this:
sudo dd if=/dev/sda of=/dev/sdb bs=1M status=progress

...where /dev/sda is your system and /dev/sdb is USB

---

### Post by C.S.Cameron on 2022-06-18
This sounds like what you may want: [https://askubuntu.com/a/1300542/43926](https://askubuntu.com/a/1300542/43926)

---

### Post by kawazu on 2022-06-21
Thanks all for your input. After digging and playing around a bit, I stumbled across [https://penguins-eggs.net/](https://penguins-eggs.net/) which seems closest to what I want/need at first glance. Now, giving this a try with a real installation. :)

---

