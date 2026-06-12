---
title: "Kinks in the Eft"
date: 2007-02-06
forum: General Help
---

### Post by booljayj on 2007-02-06
I have been having a little trouble with Edgy Eft. First off, I'll give you an at-a-glance look into all the relevant information for my computer:

AMD64 3500+ CPU
GeForce 6100 integrated graphics
1 gig RAM
WMP54G Wireless LAN Card
Dual-Boot: Ubuntu 6.10 and Windows XP MCE
Screen resolution: 1280x1024 (76 Hz)
Almost completely new OS except for a few automatic updates.

The problems I have been having are extremely annoying and almost impossible to work with. I'll list them out for the sake of clarity.

A) Graphics aren't working right. Whenever I move a window or scroll a page, I can actually see the screen refreshing itself line after line as the moving body jumps from place to place. At 76 Hz, you would think this impossible. Also, if I use the System Monitor I can actually see it max out my CPU just for moving a window, and the CPU Idles at around 20% without anything running. Ubuntu recognizes the GPU, or at least acknowledges that it exists in this computer, so that's not the problem. My hypothesis: Ubuntu is using my CPU to render all graphical effects, and completely ignoring my graphics processor. Why would it do this, and how do I fix it? I hope to one day be able to use Beryl, but I can't due to current limitations.

B) My Internet does not connect. This is not so much as a problem as a clarification. You see, I have already read that my particular wireless card does not work with Edgy. However, anything beyond that is murky. Some say that, using ndiswrapper, I can get it to work. Others state that it simply will not work without modifying the kernel itself. What exactly is the current consensus on this issue? Will ndiswrapper work? In fact, is there and easier way still?

C) My windows NTFS drive, named hda1 and located at /media/hda1/, is read-only. Is this simply because it is a drive used by a different OS, or is it perhaps because it is NTFS? I highly doubt the latter, knowing full well the flexibility of Linux systems, but it couldn't hurt to check. So, why is the drive read-only and how can I change it?

D) Being able to use LMMS was one of my main reasons for using a dual-boot. I know that Ubuntu has some sort of package for it, but it doesn't seem to be in the convenient add/remove applications database. How would I go about installing it? I've heard of apt-get, but don't really know how to use it.

Problem (A) is the most important one for me at the moment, but the rest are still needed. I appreciate any help anyone could give me.

---

### Post by gradedcheese on 2007-02-06
b) yeah, I think it's still ndiswrapper for the WMP54G (broadcom) cards.  This is basically a wrapper under which you install the Windows driver and supplied firmware, a temporary solution (hopefully) until a real driver is made available or written.

C) yes, it's read-only because the stable NTFS 'driver' can only manage that so far.  You can, however, install different software to get read/write, try google for "ubuntu ntfs" or search the forum.  I don't know much more about it since I don't have any NTFS stuff here, but I have heard that it's possible to use it, just not with what ships by default.

EDIT: ah, also I see here: [http://www.ubuntuforums.org/showthread.php?t=354263](http://www.ubuntuforums.org/showthread.php?t=354263) that NTFS write support can be enabled pretty easily, you might want to give it a try.

---

### Post by mcduck on 2007-02-06
a) Have you installed nVidia's drivers?

d) LMMS is not in the Add/Remove-thing, but it's in the repositories. Just open Synaptic (System/Administartion/Synaptic) and search for lmms ;) If it doesn't show you need to enable Universe repository.

---

