---
title: "MSI GS70 won't init nvidia unless USB mouse is plugged in (13.10)"
date: 2014-02-18
forum: General Help
---

### Post by geordan on 2014-02-18
I have bizarre behavior with my MSI GS70 laptop running Ubuntu 13.10.

If I turn on the machine with no USB devices plugged in and select Ubuntu from the Grub menu, it hangs at a blank purple screen.  It does this even if I add "nomodeset", "vesafb.nonsense=1", "nosplash".

However, if I plug in a USB mouse and turn the machine on, Ubuntu boots normally into Unity.  How does that work?  How can I set it up so that I don't have to have a USB device plugged in every time I want to boot?

Once the machine is on I can sleep and wake the machine just fine.  It appears to be a problem only during boot.

For reference, this is an Optimus machine; I'm running nvidia-331 and bumblebee from the xorg-edgers PPA.

---

