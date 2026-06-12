---
title: "Can't see keyboard text at login (GUI) screen after nvidia driver upgrade?"
date: 2014-02-03
forum: General Help
---

### Post by Butthead on 2014-02-03
Hi,

Have a slight problem here.  Everytime I try upgrading the Nvidia graphics driver to a newer version, I get stuck at the Kubuntu login GUI at the next reboot (can't seem to  type in any text into the "password" box).  This has happened to me once on a system upgrade, and recently when using "additional drivers" to try upgrading the graphics card driver to a newer (recommended) version that they showed.  Google search seems to turn up nothing for me about how to go about fixing this.  Getting tired of reinstalling the system all the time.  I'm using the most recent version of Kubuntu 12.04(04, I think?) LTS.  Graphics card is a GeForce 8200 (I think, since I'm using the live CD  to type this?).  I'd really appreciate any help in getting this fixed!

---

### Post by Butthead on 2014-02-04
Seems to have figured it out.  Turns out newest Nvidia driver (311.02?) in Additional Drivers was buggy when it installed itself on my video card.  Followed **Answer 1** on this webpage.  Only changes I did was install **Kubuntu** desktop (instead of Ubuntu), and used Additional Drivers to re-install the 304.116 Nvidia driver after purging the newer one (sudo apt-get install nvidia-304 seemed to install a non-working Nvidia settings GUI on the system).

[http://superuser.com/questions/651596/ubuntu-12-04-lts-blinking-cursor-and-cannot-start-after-nvidia-driver-upgrade]("http://superuser.com/questions/651596/ubuntu-12-04-lts-blinking-cursor-and-cannot-start-after-nvidia-driver-upgrade")

---

