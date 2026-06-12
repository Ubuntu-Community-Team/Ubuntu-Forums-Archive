---
title: "Using ATI and NVIDIA card in the same system"
date: 2008-05-12
forum: General Help
---

### Post by sicofante on 2008-05-12
I have an ATI integrated graphics motherboard and I recently bought a very cheap Nvidia card because the ATI drivers are not handling compiz well yet.

I'll be getting a second monitor soon and I was thinking if there's a chance to run both cards at the same time? That would allow me to check for differences in performance and compatibility.

---

### Post by EvenStevens on 2008-05-12
No. You can't run two separate graphics processors at once unless they're in SLi or Crossfire mode (for which you need 2 cards exactly the same). 
Note, this applies for ANY operating system.
It's either one or the other.

Your new graphics card will have a dual output so you can run 2 monitors like that.

---

### Post by lordxale on 2008-05-12
EvenStevens is unfortunately misinformed.

Of course you can run two video cards in non crossfire/sli mode (For the purpose of having multiple monitors).  I haven't done it too much, but I used to have a sweet AGP GeForce 256 32mb and a PCI ATI Rage 128 Pro 16mb that I used to run dual monitors off of from Ubuntu...oh, probably 5.10 or something.  Everything I've run since then has been dual monitors on one card.

That said, in my experience when you add a PCI/AGP/PCIE video card to a system with integrated graphics, the motherboard BIOS automatically disables the integrated and usually there seems to be no way to re-enable it so you can use both.  A friend of mine used to have an old Athlon-XP-based E-machine that I convinced to run two PCI Geforce4 MXs and the integrated S3 graphics all at the same time for 5 monitors (on Windows XP, anyway) No joke - the guy is a day trader.  Sickest monitor setup I've seen in person, and I put it together!  But it seems that that kind of luck is few and far between.

If you can add the card, though, and see that the onboard graphics are still enabled in BIOS, you should be good - verify that the computer sees both graphics cards by doing an lspci from the command prompt.  After that, hopefully we can find some other expertise to write your xorg.conf.  AFAIK, you won't be able to run fglrx and nvidia-glx at the same time, though, so one of them will be limited to the open source drivers (radeon and nvidia, respectively).

If somebody CAN figure out how to run nvidia-glx and fglrx in the same system, though, I'd love to hear about it!

04:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
05:00.0 VGA compatible controller: nVidia Corporation NV41 [GeForce 6800 GS] (rev a2)

:smile:

---

