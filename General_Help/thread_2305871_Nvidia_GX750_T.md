---
title: "Nvidia GX750 T"
date: 2015-12-10
forum: General Help
---

### Post by Billy_Martinez on 2015-12-10
NVIDIA is the worse company to deal with when it comes to Linux. I have a Nvidia GX750 TI video card and I got a better hard drive so I'm trying to do a fresh install on my machine and for some reason the video card driver is not working.

1. I booted into the ubunut installation with the no mode set option.
2. I download and installed the NVIDIA-Linux-x86_64-352.63.run driver from their website.
3. After the installation I rebooted the machine and I got an error message that my machine in running in low graphics mode. 

Those steps worked last time so I don't understand why they aren't working now! I've been at this for two hours already this is ridiculous.

---

### Post by buzzingrobot on 2015-12-10
Is there a reason you aren't using the Additional Drivers tool?

If Nvidia provides guidance on backing out a failed install, do that first

---

### Post by SeijiSensei on 2015-12-10
There is almost never any reason to download the drivers from NVIDIA.  I have the same card and am using 346.x.  I installed it from the command line with
```

sudo apt-get install nvidia-346

```
You can see the array of drivers available in the repositories with
```

apt-cache search nvidia

```
You'll see the 304, 331, 340 and 346 drivers in the repo for 14.04.  I didn't have much luck with 331, which was the current driver at the time I bought my card, but 346 works fine.

---

### Post by andrew.46 on 2015-12-10
FWIW I have a GTX 750 Ti and I am running 352.63 with absolutely no issues on a 64bit system. I confess to being between Ubuntu installations at the moment but the general idea of card + driver version still holds true...

---

### Post by efflandt on 2015-12-10
A potential issue with using a .run script is that it might not be compatible with everything on the system, will not update automatically, and in the past usually needed to be rerun following a kernel update (not sure if that is still an issue). If you use Ubuntu packages then everything should work together and update properly.

I originally installed my GTX 750 Ti and then 14.04.1 Jan 2015 and at that time both default nouveau and nvidia-current package did not support it (although, it worked with nvidia-current in 12.04). So I booted recovery, enabled networking, and went to a root terminal to purge nvidia-current, install nvidia-331-updates, and that worked fine after rebooting. I am currently running nvidia-358 package from graphics-drivers/ppa.

---

### Post by Billy_Martinez on 2015-12-10
> **SeijiSensei said:**
> There is almost never any reason to download the drivers from NVIDIA.  I have the same card and am using 346.x.  I installed it from the command line with
```

sudo apt-get install nvidia-346

```
You can see the array of drivers available in the repositories with
```

apt-cache search nvidia

```
You'll see the 304, 331, 340 and 346 drivers in the repo for 14.04.  I didn't have much luck with 331, which was the current driver at the time I bought my card, but 346 works fine.

Thanks this fixed my problem.

---

