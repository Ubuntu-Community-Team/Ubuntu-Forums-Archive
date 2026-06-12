---
title: "linux-headers-2.6.15-21-386"
date: 2006-07-05
forum: General Help
---

### Post by lullebakman on 2006-07-05
[LEFT]I'm trying to install the ati drivers but I have 3 kernels on my box:
[LIST=1]
[*]2.6.15-21-386
[*]2.6.15-23-386
[*]2.6.15-25-386[/LIST]I have to compile these drivers for each kernel I have, but the packages needed to compile aren't anymore available for 2.6.15-21-386.

It is currently stuck at "E: Couldn't find package linux-headers-2.6.15-21-386"
(I have the dutch version, so this is a raw translation that can be incorrect).
Maybe I'll even need some other older packages.

So, the possible solutions:

[LIST=1]
[*]Someone has still got the old linux-headers-2.6.15-21-386 package
[*]Someone knows a depot for older packages (not found on packages.ubuntu or packages.debian)
[*]Someone knows how to remove the old kernel correctly so I won't need the package[/LIST]Thank you
[/LEFT]

---

### Post by jocko on 2006-07-05
> So, the possible solutions:

   1. Someone has still got the old linux-headers-2.6.15-21-386 package
   2. Someone knows a depot for older packages (not found on packages.ubuntu or packages.debian)
   3. Someone knows how to remove the old kernel correctly so I won't need the package

Answer to #3 (which I guess is the best and simplest solution unless you have any reason to keep the old kernels):
```
sudo apt-get remove linux-image-2.6.15-21-386 linux-image-2.6.15-23-386
```
This will remove both of the older kernels and update the boot loader to only point to the remaining version.

Hope this was what you wanted..

---

