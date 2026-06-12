---
title: "Bootup Problems"
date: 2007-06-26
forum: General Help
---

### Post by Peder_Erickson on 2007-06-26
I just installed Ubuntu 7.04 on my computer, it all went very well, but after I installed the drivers for my NVidia card, the X server stopped working.  if i have my computer use the NVidia card instead of the onboard, it crashes while booting

The only way I can use ubuntu is if i have the origonal xorg.conf, and am using onboard video

im using a NVidia Geforce FX 5200, on a Compaq SR1023WM
1 gig of memory, Dualboot with Windows XP

---

### Post by avik on 2007-06-26
How exactly did you install the drivers (through apt-get or via the .run file)?  What errors are you getting when X crashes?

---

### Post by Peder_Erickson on 2007-06-26
I downloaded the Nvidia-glx drivers through Symantic

The crashes basically say that there are no screens attached, even though i have 1 attached to the NVidia card at all times, and the other is currently connected to the onboard gfx card

---

### Post by UK-Wobbie on 2007-06-26
> **Peder_Erickson said:**
> I downloaded the Nvidia-glx drivers through Symantic

The crashes basically say that there are no screens attached, even though i have 1 attached to the NVidia card at all times, and the other is currently connected to the onboard gfx card

I use to get that all the time when i install my Nvidia drives! Now i fixed it by installing the new Nvidia drives.

Look for Nvidia-new in your download list manu

---

### Post by avik on 2007-06-26
> Look for Nvidia-new in your download list manu

It's actually nvidia-glx-new.

---

### Post by Peder_Erickson on 2007-06-28
what do you do to make the NVidia card the default card?

When i clicked the checkbox in the restricted drivers manager, it just changed the driver for the onboard card... which disabled X until I switched the driver in the xorg.conf

---

### Post by avik on 2007-06-28
> what do you do to make the NVidia card the default card?

For me, installing the driver through apt-get enabled it, but I think the command to enable it manually is:

```
sudo nvidia-glx-config enable
```

---

### Post by Peder_Erickson on 2007-06-28
There must be something wrong with my computer.  I cannot get it to work at all.

It seems that now i'm stuck at 640X480 resolution on my old card, and unable to use my new card in linux.

---

### Post by Peder_Erickson on 2007-06-30
Thanks for all the help, got it working by messing around in the xorg.conf file

Now I can't wait to see what Linux can do with a good video card \\:D/

---

