---
title: "Goldilocks, 12.10, and an Nvidia GT440"
date: 2012-11-18
forum: General Help
---

### Post by linux4me on 2012-11-18
I feel like Goldlilocks, but instead of beds and porridge I've been dealing with the an Nvidia GT440 and the video driver options in Ubuntu 12.10.

I did a clean install and was using the nouveau driver. However, it gave me intermittent video corruption, which conveniently occurred when I was trying to change to one of the nvidia proprietary drivers so I could get the attached screen shot.

I installed linux-headers-generic (which is a dependency for the proprietary nvidia drivers, but is apparently not included), then tried nvidia-current.

With nvidia-current, grub displayed in a whopping 640 x 480 resolution and within seconds of getting to the desktop, which was at the correct resolution for my monitor (1280 x 1024), I would get a reproducible error message about evolution-calendar-factory, part of the evolution-data-server package, crashing. I'm not using Evolution, but apparently the evolution-data-server package is installed by default and may have something to do with the time/date display. 

Next, I tried nvidia-current-updates. With it installed, grub was still at 640 x 480, the desktop was normal, but with autohide on for the launcher, my mouse would not get the launcher to come out of hiding. I could get it to appear by using the Winblows/meta key, but I'm looking for "just right," and that isn't it.

So I tried nvidia-experimental-304. Grub is now back to it's normal 1280 x 1024 resolution, no changes in /etc/default/grub were necessary, and everything seems to be working fine. I haven't had any video corruption and the launcher is behaving normally. So far at least, nvidia-experimental-304 is just right. I thought I'd post this in case anyone else is experiencing the same kind of issues and might share my initial hesitancy to install a driver labelled "experimental."

Here's the process I went through to install the 304 driver in case anyone wants to try it:

```

sudo apt-get install linux-headers-generic

```

```
sudo apt-get install nvidia-experimental-304
```

Then just reboot and give it a try.

---

