---
title: "compaq presario v2000 - wifi problem"
date: 2015-06-17
forum: General Help
---

### Post by goltingn1 on 2015-06-17
Have [COLOR=#000000]compaq presario v2000 with lubuntu 12.10. Wifi off. No internet connections. bcm4306/3 chip.
Download b43-fwcutter install, next download from [/COLOR]mirror2.openwrt.org broadcom-wl-5.10.56.27.3_mipsel.tar.bz2 drivers.
Copy package broadcom-wl-5.10.56.27.3 from archive to /lib/firmware/, next
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.owhat is my next step? Thnks!

---

### Post by kerry_s on 2015-06-17
the b43 drivers are on the installer, just plug the usb/cd whatever you used to install & run "additional drivers".

oops, just noticed the 12.10, does that have the additional drivers app ?
suggest you use a more updated lubuntu version. if you check the 4th option(extra codecs) on the installer when you install off line it will install them so you will have wifi when it reboots.

---

### Post by goltingn1 on 2015-06-17
My [COLOR=#000000]additional drivers" window is empty. Does not have additional driver for my broadcom wifi...[/COLOR]

---

### Post by kerry_s on 2015-06-17
i had a feeling they didn't do that in older versions. i only found it recently when i installed off line, using ubuntu-mate 15.04.

---

### Post by Bucky Ball on 2015-06-17
Welcome. 12.10 is no longer supported. There are no repos for it and so you cannot update or upgrade (in other words, you can't install anything from the 12.10 repository). 12.10 is no longer officially supported by Canonical and you will find it difficult to get much help for it here. It is not a good idea to use an unsupported release online. 12.10 has not received security updates, or any other kind, in about a year.

Please install a supported release, I suggest 14.04 LTS, supported until 2019, and post a new thread if the problem persists. (Note: non-LTS interim releases are now only supported for nine months). 

Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730") for staff upgrade recommendations. Post a new thread if you need help installing a recent release. Feel free to post a link to that thread here. Good luck. :)

PS: You do not need to do most of what you're doing in post #1 to get B43 working. It is all in the repos, shouldn't be the need to install anything from anywhere else. Once on a supported release,  boot, update the install, you should be offered drivers for the wireless card or it should work 'automagically'. Broadcom, particularly the older cards, are very well supported now.

---

