---
title: "Cannot Run Installer"
date: 2013-01-05
forum: General Help
---

### Post by Rsjc741 on 2013-01-05
Hey guys, I'm back again.. once again complaining about my wonderful graphics card, the Nvidia GTX 560 Ti (PNY varient).

So to get us started, here's a list of what usually happens when I try and install most types of Ubuntu/any other flavors of Linux:

- Configure BIOS to set IOMMU on w/ 64-bit conversion (*I get memory errors if I don't)
- Load Ubuntu / Kubuntu
- Select "Install Ubuntu" (most options lead to #3 however)
- Stuck on the screen attached below
OR
- Prompt loads, follow through with installation.

- Loads OS first time, no problems
- Installs Wifi drivers, current Nvidia Drivers (either 304 / 310)
- Installs latest updates and patches
- Restarts
- Boots up
- Xserver Crashes
- I sit at a console for eternity.


So TL;DR...

- Nividia's drivers make Xserver crash
- Bundled drivers make my install screen glitchy and unusable.

(See below)


Here's my setup:

Asus M5A97 Motherboard
PNY Nvidia GTX 560 Ti Graphics Card
16Gb Corsair Vengeance series RAM
AMD Fx-8150 (8-core) CPU
1, 128Gb SSD
1, RAID 0 (1tb x 2hdd) array


I haven't really got much help here... and I've had this problem for a couple of years.
Even with my experience, I really have no idea how to fix this.

Experts, help?

Thanks so much.

(Screen image on boot into Ubuntu for installation)

[IMG]http://s14.postimage.org/gm166lq4x/CAM00001_1.jpg[/IMG]

---

### Post by Rsjc741 on 2013-01-06
Bump.

I really need some help here.

No graphics drivers = no monitor support or effects.

I can't spend my whole Linux life on a VGA resolution.

---

### Post by Muratturat on 2013-01-06
> **Rsjc741 said:**
> Bump.

I really need some help here.

No graphics drivers = no monitor support or effects.

I can't spend my whole Linux life on a VGA resolution.

Does ubuntu recognize graphics drivers?
Put this ugly command to terminal, what it say?
```
lshw -c video
```

---

### Post by Rsjc741 on 2013-01-06
Im reinstalling Linux Mint and seeing if I can get some direct-download drivers to work better than downloaded ones via Prop. hardware.

I'll test out both the 32-bit and 64-bit version and give you a readout of what each says.

---

### Post by Muratturat on 2013-01-07
> **Rsjc741 said:**
> Im reinstalling Linux Mint and seeing if I can get some direct-download drivers to work better than downloaded ones via Prop. hardware.

I'll test out both the 32-bit and 64-bit version and give you a readout of what each says.


I think problem is starts from OP drivers.

When the OP has opened do not restart.
Go to [http://www.geforce.com/drivers/results/52240](http://www.geforce.com/drivers/results/52240)
Download it
Go to [http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/](http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/) there you will find information how to install them.

---

