---
title: "Uninstalling Linux"
date: 2007-09-25
forum: General Help
---

### Post by Josh_NC on 2007-09-25
I would like to uninstall linux from my system. I have my system dual booting between Linux and Windows XP. I want to keep Windows XP on and take Linux off. How do I go about doing that without ruining my Windows XP partition on my hard drive.

I am going to put a different version of linux on :)

---

### Post by oilchangeguy on 2007-09-25
this is fairly simple. insert the cd from whatever version of linux you are going to use, boot from it, and have it install on your present ubuntu partition. and always, always, back up your data from windows, ubuntu, whatever, before you attempt to change anything.

---

### Post by LaRoza on 2007-09-25
> **Josh_NC said:**
> I would like to uninstall linux from my system. I have my system dual booting between Linux and Windows XP. I want to keep Windows XP on and take Linux off. How do I go about doing that without ruining my Windows XP partition on my hard drive.

I am going to put a different version of linux on :)

You could just install over it, using the same partition and swap, that might be easiest if you don't intend on changing the partition layout. 

You could also do a triple boot, it is not difficult. I have gotton 12 Operating Systems on one computer, one of them was XP. (This was on one hd, at the same time)

---

### Post by martalli on 2007-09-25
At this point, the initial linux installation is already done.  However, if you keep a separate /home partiton then you could reinstall linux (same or different distro) to your heart's content on the / partition.  I have used a few different distro, but most will be happy with a root partition and a /home partition.  IIRC fedora likes to have a tiny /boot partition, but in any case remember not to format your home partition, choose the exact same name as your old account, and wallah, you will be back in the same old home and desktop as before.

You may have some conflicts between the old distro's GNOME or KDE setup, so mv'g the .kde and .gnome directories would be nice if you want to have the default setup for your new distro.

---

