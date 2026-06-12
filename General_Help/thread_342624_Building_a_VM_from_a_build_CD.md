---
title: "Building a VM from a build CD"
date: 2007-01-20
forum: General Help
---

### Post by fritz_monroe on 2007-01-20
I've been happily running Ubuntu on my laptop for a bit over a year.  The problem is my school has several pieces of software that I have to use and these are strictly Windows, so I have to dual boot.  I figured that I could make a virtual machine and boot into XP to do this work.  The problem is my laptop came without a CD and I created the build CDs from the "hidden partition."  I briefly looked into building a VM using this and when creating it, the system complained that this was not a compatible system for the build.

What I'm trying to find out if there's a way that I can build this VM with these CDs.  I paid the Windows tax on the laptop, so I should be able to make use of the software.  A pointer to a tutorial or how-to would be great, but any info would be appreciated.

My system info is Sony VGN-FS742/W laptop with 2 gig RAM.  I'm running Ubuntu 6.06 LTS and have installed all software updates.  

Thanks in advance for any help.

---

### Post by Jose Catre-Vandis on 2007-01-20
No quite sure what you mean - do you have physical install CDs for Windows/Ubuntu or iso files on hard drive? Which VM p[roduct do you intend to use? Vmware, Qemu ? If you already have windows onboard, why not dual boot?

---

### Post by lamego on 2007-01-20
If I understand it correctly you are trying to install an Windows XP build developed for your specific laptop into a VM.
Please contact your hardware vendor for this, it was him which provided you an "hw locked" windows xp copy.

---

### Post by fritz_monroe on 2007-01-20
That's exactly what I'm trying to do.  That's why I'm asking here to see if it's even possible.  I'm trying to install the build that was developed for this laptop onto this laptop.

As for dual booting, I'm doing that right now.  But it's such a PITA to have to shutdown and boot into XP that I'd rather get the VM thing worked out.  What I tried was using Qemu to build the VM and VMPlayer to use the build.

---

### Post by Jose Catre-Vandis on 2007-01-20
Well it "might" work, but my experiences with putting an existing "image" of Windows (XP) into another hardware environment (real, not virtual) is that XP gets very upset and usually requires a repair installation to get the hardware issues sorted out. I would guess this might be the same in a virtual environment, although it might just be OK?? You might also have licensing problems if you connect up to the net because WGA will not be expecting different hardware (even though it is virtual) ?? if you are running both the real XP and the virtual one on the same key. If your build CDs will allow you to install from scratch, then XP should just pick up on the hardware in the VM, unless as Iemago says, it has been hardware locked.

---

