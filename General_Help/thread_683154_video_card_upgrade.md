---
title: "video card upgrade"
date: 2008-01-30
forum: General Help
---

### Post by tonymoloney on 2008-01-30
My Gutsy system is very stable and does just about everything I want.
However, to be perfect, it needs an upgrade to the video card.
My question is this, if I install an upgraded video card, do I have to re-install Gutsy so that it can be recognised, or do I just find the correct drivers and add them in somewhere?

---

### Post by taurus on 2008-01-30
If you replace the current video card with a new one, you only have to reconfigure your X server again to use the new card.  No need to reinstall anything.  

Shutdown your machine and replace your video card.  Then, boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
Once your machine is up again, go into System -> Administration -> Restricted Driver Manager and install a driver for it.

By the way, what graphic card do you have right now and what do you plan to replace it with?

---

### Post by tonymoloney on 2008-01-30
Thanks taurus, that's the advice I need.
My current video card is whatever the onboard VGA is, and I will look around for a good deal on any AGP or PCI card. I don't have PCI Express on this mobo.

---

### Post by taurus on 2008-01-30
Make sure you go into the BIOS and turn off the onboard graphic card controller when you install an AGP video card.

---

