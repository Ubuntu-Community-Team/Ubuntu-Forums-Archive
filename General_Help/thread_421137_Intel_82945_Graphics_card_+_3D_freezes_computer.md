---
title: "Intel 82945 Graphics card + 3D freezes computer"
date: 2007-04-24
forum: General Help
---

### Post by vidak on 2007-04-24
I have an Intel Corporation 82945G/GZ Integrated Graphics Controller, which is driving me crazy... When using any 3D application like beryl or armagetron or whatever, the machine freezes after a random time, with some stripes on the screen. There is no log entry, or whatever, I cannot get a console, even NumLock is dead, only the power button is working
I've already tried the i810 and intel drivers, the error is the same...
any ideas? someone with similar problem?

---

### Post by qhartman on 2007-05-24
This kind of freeze is very often a result of faulty RAM and/or overheating. I'd suggest running a RAM test overnight and seeing if that turns up anything. You can do this by selecting "memtest86" from the boot menu when your computer first comes up, or from an Ubuntu boot CD.

What release of Ubuntu are you using?

---

### Post by vidak on 2007-05-24
> **qhartman said:**
> This kind of freeze is very often a result of faulty RAM and/or overheating. I'd suggest running a RAM test overnight and seeing if that turns up anything. You can do this by selecting "memtest86" from the boot menu when your computer first comes up, or from an Ubuntu boot CD.

What release of Ubuntu are you using?

It's feisty. The problem was present however under edgy, too. And the same bug(?) happens on an other computer with the same hw configuration, and only when running 3D software...

---

### Post by qhartman on 2007-05-29
A lot has changed in the driver infrastructure and whatnot since edgy. It would surprise me somewhat that a bug exists that seems so fundamental that survived that many revisions. Your description of the failure still makes me think it's a hardware issue.

BIOS Update?

Heat? Do the chips on your motherboard have heatsinks and/or fans on them? Are the fans working? If you take the case cover / panel off and direct some air flow into the computer, does it seem to make a difference?

---

### Post by vidak on 2007-05-30
> **qhartman said:**
> A lot has changed in the driver infrastructure and whatnot since edgy. It would surprise me somewhat that a bug exists that seems so fundamental that survived that many revisions. Your description of the failure still makes me think it's a hardware issue.

BIOS Update?

Heat? Do the chips on your motherboard have heatsinks and/or fans on them? Are the fans working? If you take the case cover / panel off and direct some air flow into the computer, does it seem to make a difference?

We got 3 computers of similar type: two is the same (with the same error) - these have intel 82945G/GZ card, and the third has intel 945G/GZ: 3D works with this one. 
The physical characteristics of the two PCs are the same: on the motherboard there is one huge fan next to the CPU's heatsink, the GPU has only a heatsink and is located next to the CPU. 
This is the same on the 3 PCs, the only difference is the grapic card's type...

By direct air flow you mean eg. a fan placed next to the PC?:confused:

---

