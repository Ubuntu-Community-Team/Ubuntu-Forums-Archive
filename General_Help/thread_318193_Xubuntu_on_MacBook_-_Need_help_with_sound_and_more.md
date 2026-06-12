---
title: "Xubuntu on MacBook - Need help with sound and more"
date: 2006-12-13
forum: General Help
---

### Post by commonmanthemes on 2006-12-13
So, I have a MacBook Pro 15" 2.0GHz.  I've already been a big Ubuntu user with it, but I wanted to switch to Xubuntu.  I thought this would be easy, but I need some help.

The sound doesn't work.  In Ubuntu, I just clicked unmute "side" and use "line in as output."  All good.  But, in Xubuntu, all the options are selected already and I don't have much else to do.  I can choose between "default" and "#0: HDA Intel".  I've mostly messed with the latter, but there's nothing I can do to get sound out.

Also, I have a Logitech Bluetooth mouse.  In Ubuntu, I had to manually connect it with "hidd --connect," but it worked fine.  In Xubuntu, it automatically connects but I can't get the scroll wheel to work.

Please help.

---

### Post by commonmanthemes on 2006-12-13
Bump.

I swear, everytime I start a thread here I never get any help...  Is it because I'm a Mactel guy and there's not a lot of support or are these just hard questions?

*grumble*

---

### Post by jasl8r on 2006-12-17
You still need to run a hidd --connect.  The mouse is not 'automatically' connecting in Xubuntu.  The macbook hardware caches any established bluetooth connections so that the hardware can be used before the bluetooth system is initialized by the OS.  This allows for the use of a bluetooth keyboard in refit / grub for instance.  Without establishing the bluetooth connection you won't be able to use the mousewheel.

---

