---
title: "Issues with a particular HDMI projector on Ubuntu (plot twist: Fedora works fine)"
date: 2018-01-31
forum: General Help
---

### Post by Roasted on 2018-01-31
Hi friends. I'm trying (and so far, failing) to find a solution to an issue I'm having. Some context, we have an assortment of different projectors, all HDMI, and an assortment of laptop hardware. The problematic projector in question is an InFocus IN126STa. What happens is when I plug in via HDMI, it picks up a signal from the laptop and I'll see something (sometimes it's extended mode, other times it's mirror), but the problem comes in when I switch modes -- say extended mode versus mirror. Almost all of the time, trying to switch the mode one time results in the InFocus projector going blank. The laptop however seems to respond as if it acknowledges the projector. I see the InFocus entry in display settings, I see the resolution, the framerate, the make/model, etc. It's just... nothing appears on the screen after trying to switch modes. I've tried this with other model projectors (namely Epson and NEC) but haven't ran into these issues.

The laptop hardware in question was tested on a Lenovo T470, Lenovo E570, and an Acer Travelmate TM113. The E570 is the almighty target machine to try and get working (hence why there's more mention of E570 below), but the Acer and T470 were just to compare. A rough list of what I've tried:

T470 with Ubuntu (Unity) 16.04 with Xorg
T470 with Ubuntu (Gnome) 16.04 with Xorg
E570 with Ubuntu (Gnome) 17.10 with Xorg
E570 with Ubuntu (Gnome) 17.10 with Wayland
Acer Travelmate TM113 with Ubuntu (Unity) 16.04 with Xorg
Three different types of HDMI cables
Upgrading the BIOS on the E570 to the latest version
Upgrading the firmware on the InFocus projector to the latest version
On the E570 with Ubuntu (Gnome) 17.10, I've tried the current Ubuntu kernel v4.13, along with mainline 4.14 and mainline 4.15
Installed Antergos (Gnome) on the E570 and updated everything
---------------------------------------------------------------------------
All of the above resulted in the same experience: no change, problem still existed.

Here's where things got interesting... a colleague runs Fedora 27 on a T470, so we tested that. Boom, worked fine. After that, I installed Fedora 27 on the E570. Again, worked fine. The problem simply went away on Fedora. Projection with the InFocus projectors was a very consistent, stable experience. 

At this point I'm trying to figure out what's different in the way Fedora 27 may handle Intel video on the E570/T470 than how Ubuntu/Antergos handle it. Something about Fedora is making this a far better experience, but given our target OS is Ubuntu, it makes me wonder what on earth it could be.

Based on this information, does anybody have any suggestions or further ideas to try? I appreciate any and all answers. :)

---

