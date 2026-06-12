---
title: "New Kernel VS New Distibution"
date: 2007-12-01
forum: General Help
---

### Post by gubemton on 2007-12-01
Hi all,

I now have ubuntu edgy installed. I did a update once and a newer kernel version appeared in my grub bootloader(on top of the old one). I tried to boot with the new kernel but certain things are lost esp. the WLAN DRIVER. DO I NEED TO REINSTALL THE DRIVER IN ORDER TO USE THE NEW KERNEL?

If I do a system upgrade to ubuntu gutsy, will my settings and driver still be there ?

Excited to hear some replies.

---

### Post by mysticrider92 on 2007-12-01
After a kernel update some drivers do have to be reinstalled (nVidia binary drivers are a good example). It all depends on how the drivers are set up for that card.

There is a fairly good chance that the card will "just work" in Gutsy with no configuration. If you upgrade, some settings will be modifed and your driver might or might not be installed. What kind of wlan card is it, and what driver setup are you using (ndiswrapper, madwifi, etc)?

---

### Post by gubemton on 2007-12-01
> **mysticrider92 said:**
> After a kernel update some drivers do have to be reinstalled (nVidia binary drivers are a good example). It all depends on how the drivers are set up for that card.

There is a fairly good chance that the card will "just work" in Gutsy with no configuration. If you upgrade, some settings will be modifed and your driver might or might not be installed. What kind of wlan card is it, and what driver setup are you using (ndiswrapper, madwifi, etc)?

Thanks for replying.

I am using bcmwl5.sys driver and ndiswrapper setup.

---

### Post by mysticrider92 on 2007-12-01
Judging by that driver file (and Google) you have a Broadcom 4-series wireless card. Appearantly these do not work out of the box on Ubuntu Gutsy, so you would have to install ndiswrapper and the driver again if you chose to upgrade.

I am not quite sure, but I don't think that you should have to install anything after a kernel upgrade if you are using ndiswrapper, so that seems kind of odd. Maybe try the new kernel with the same steps you used to get it working the first time? If it doesn't work, the kernel could have something configured differently that will not work right with the way your driver was installed.

Also, since Edgy is now a year old, you will possible have a harder time getting updates, but I don't know how much of a problem that is.

---

