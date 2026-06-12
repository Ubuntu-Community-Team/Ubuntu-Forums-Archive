---
title: "pendrive Ubuntu 8.04"
date: 2008-06-26
forum: General Help
---

### Post by DrScum on 2008-06-26
I was trying to make a ubuntu 8.04 pendrive using the live CD and the instructions available on this forum and on pendrivelinux.com.

I was not able to get the persistent mode going. During the preparation of the pendrive at the point were you generate the casper partition there was an error message regarding the w option. Later on when trying to use the persistent mode i.e. rebooting after having modified the desktop, the system doesn't allow to boot with an error message suggesting that the partition is not writable. 

I read the post and bug reports regarding the permissions problem and found that the initrd.gz file I was using did not include that error. I don't know how to proceed now. Is anyone out there who could point me to a tutorial, preferably a verbose tutorial, which guides me through the process successfully?

---

### Post by mfdc1969 on 2008-08-12
I am at the same point with my Live USB Pendrive ... I followed the instructions on the Community page [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") using Method 0.

I downloaded a NEW .iso image of hardy 8.04.1 as the older Hardy .iso didn't work - my attempts to create a Live USB Pendrive crashed after about 5 minutes. Method 0 is:
[INDENT]
**Live USB creator (GUI-based, runs from Live CD)**

[I]Live USB creator automates the process of creating a bootable Live USB system from a running Ubuntu Live CD. Simply run the Live CD, install the tool and start the Live USB installation from the System administration menu.

[https://launchpad.net/liveusb](https://launchpad.net/liveusb) -- probono

(A better link: [https://launchpad.net/liveusb/+announcements](https://launchpad.net/liveusb/+announcements) which explains that you run the livecd and the you click on the link: [http://ppa.launchpad.net/probono/ubuntu/pool/main/l/liveusb/liveusb_0.0.9_all.deb](http://ppa.launchpad.net/probono/ubuntu/pool/main/l/liveusb/liveusb_0.0.9_all.deb) )[/I][/INDENT]

The installation to my 4GB USB 2.0 pendrive took about 15-20 minutes and it boots correctly and is fully functional just as a LiveCD. 

But any changes made are not saved.

---

