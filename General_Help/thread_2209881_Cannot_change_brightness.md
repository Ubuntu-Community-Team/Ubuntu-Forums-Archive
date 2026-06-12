---
title: "Cannot change brightness"
date: 2014-03-07
forum: General Help
---

### Post by Jacob_M on 2014-03-07
Hi everyone, 

Installed 12.04 LTS on my Lenovo y500. Man, Ubuntu has come really far the last couple years. It is amazing these days! Blow Windows 8 out of the water! 

Anyway, I cannot change the brightness level of the display. I use Function and the 'up brightness' key. The icon shows the brightness being turned down, but nothing happens. Any ideas? I'm still a newb so I need it broken down into dummy terms.

Thanks

Jacob

Ubuntu 12.04 LTS 64-bit/Windows 8.1 64-bit Dual Boot
Lenovo Y500
Nvidia Geforce GT 650M

---

### Post by david98 on 2014-03-07
Go to settings then click brightness and lock icon and change the setting via the brightness bar to your preferred setting.

---

### Post by Frogs Hair on 2014-03-07
Try opening Brightens & Lock and using the slider in the GUI . Sometimes drivers for function keys aren't available in Linux.

---

### Post by Jacob_M on 2014-03-08
> **Frogs Hair said:**
> Try opening Brightens & Lock and using the slider in the GUI . Sometimes drivers for function keys aren't available in Linux.

Nope. That did not work. 

Any other suggestions?

---

### Post by sam_baker2 on 2014-03-09
You can use xgamma as a kludge until you get more info.

In Terminal:
```

xgamma -gamma 1.0 

```

example:
1.0 is normal
less than 1.0 will darken   ( example          xgamma -gamma 0.8  
more than 1.0 will lighten  ( example         xgamma -gamma 1.4  )

experiment, needs to be reset after every reboot.

---

### Post by OrangeCrate on 2014-03-09
> **Jacob_M said:**
> Hi everyone, 

Installed 12.04 LTS on my Lenovo y500. Man, Ubuntu has come really far the last couple years. It is amazing these days! Blow Windows 8 out of the water! 

Anyway, I cannot change the brightness level of the display. I use Function and the 'up brightness' key. The icon shows the brightness being turned down, but nothing happens. Any ideas? I'm still a newb so I need it broken down into dummy terms.

Thanks

Jacob

Ubuntu 12.04 LTS 64-bit/Windows 8.1 64-bit Dual Boot
Lenovo Y500
Nvidia Geforce GT 650M

Hi Jacob,

I'm a Lenovo guy too. If you can't find a fix using 12.04, there's a couple of other things you could try...

First of all, did you install from the latest point version (12.04.04)? That will give you the latest drivers for your box through the kernel upgrade.

If so, then try this. Burn a disk, or create a USB image of 13.10, and see from there if your problem has been fixed. (No need to install unless it fixes your problem - just try it from the live image.)

If that doesn't work, try this. Do the same as #2 with the latest daily of the new LTS, 14.04, scheduled for release April 17th, and see if that new kernel contains the needed driver. If it does, and it fixes the problem, being a "newbe", as you say you are, I'd probably just reboot, and wait the next several weeks until 14.04 is released.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Good luck.

---

