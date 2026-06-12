---
title: "kernel panic on fresh install after update"
date: 2017-03-20
forum: General Help
---

### Post by zac13 on 2017-03-20
Hello all.

I recently reinstalled 16.04, as i had been tweaking about, and after updating to kernel 4.4.63 (i think), everytime i would attempt to login at the GUI, it would panic (flashing capslock) and i would have to hard reset. The only latest kernel that would actually work was 4.4.52.

I chalked this up to my tweaking, and attempted a fresh install, which worked with kernel 4.4.21 that came with the iso. 

After the boot into the fresh install, i went through the typical updates through apt, which downloaded and installed kernel 4.4.71 (or whichever it currently is a/o 3/20), i had another kernel panic.

At this point, i'm not really sure what else to do, as i like using Ubuntu, though if i cannot use the updated kernel whenever it rolls out, i don't see much point in continuing. 

Hardware is: 
ASUS N53SN-XV1
Core i-5 2410m
Using an Edimax USB wireless adapter, as the qualcomm atheros in this laptop has been unreliable...
Nvidia 550m

If any of the gurus around here have any advice, then i'd love to try it out. Ubuntu has been the daily driver on this thing since 14.04, which always worked without (too much) issue.

Many thanks.

---

### Post by alexandari on 2017-03-21
You can log and inspect the kernel panic using this [https://wiki.ubuntu.com/Kernel/CrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe)

The panic is probably caused by a driver provided with the new kernel. That does not mean you cannot upgrade the kernel after the new minor version is released, just seems that some driver is causing an issue. Please provide the crash report and we will analyze it

---

### Post by zac13 on 2017-03-21
Well, on a lark, i unplugged the Edimax USB wifi adapter, and the latest kernel starts up with no issue.

... meaning i did a fresh install for basically no reason. 

At least i know what's doing it, though i do have to use the atheros card now. 

Thanks much for the recommendation, alexandari. If I'm ever feeling fed up enough with the internal wifi card, i can do what you recommend and see if I can't figure out the driver issue for the Edimax.

---

