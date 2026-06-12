---
title: "New Kernel, Ubuntu Won't Boot?"
date: 2013-04-15
forum: General Help
---

### Post by seande on 2013-04-15
Hello guys, I posted a thread about a month back detailing my issues with AMD Catalyst Control, thinking that the graphics card was to blame. While AMD CCC does indeed cause issues for me, I have also found that a fresh install of Ubuntu 12.04 LTS updated to the 3.5.0-27-generic kernel will fail to load Ubuntu, or, if it does, no display is detected. No graphics drivers have been installed at this point either, as I simply ran sudo-apt-get upgrade. 

Now, I believe I know how to solve this, but feel free to offer any advice. Previously, I locked the kernel version to 3.5.0-23-generic (what 12.04 ships with I think) via Synaptic.

So my question then is, why does the updated kernel cause this issue? Is there anything I can do about it?

Thanks for any help! :)3

---

### Post by seande on 2013-04-15
Just an update, I installed the latest experimental drivers (13.3, b3) for my Radeon HD 7750. After booting into the new kernel, everything is terribly slow. The Dash takes three or four second to open after click, items within the menu load extremely slowly (wifi icon appears to be refreshing, but at a far slower pace than intended). 

I installed the graphics drivers under the old 3.5.0-23-generic kernel, so I'm assuming they must be uninstalled and rebuilt for -27? Is this correct? Why is this? Additionally, how would I do this since I cannot boot into 3.5.0-27 without the drivers?

---

