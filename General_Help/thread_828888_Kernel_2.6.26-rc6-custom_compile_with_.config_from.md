---
title: "Kernel 2.6.26-rc6-custom compile with .config from stock kernel: ALSA config missing?"
date: 2008-06-14
forum: General Help
---

### Post by pedrogfrancisco on 2008-06-14
TL'DR ppl: scroll down to last paragraph ;)

Hi!

I feel bad posting about a kernel compile in General Help, but couldn't find any category more adequate ^^.

Anyway due to some problems with my laptop I decided to do a custom kernel compile. I copied the /boot/config-2.6.24-18-generic I had to the kernel tree, loaded it in make menuconfig, saved it and compiled [used [this]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild") wiki page].

Upon reboot I found out I had no sound and no wireless. Ok, no big issue, I can use make menuconfig to build those drivers but the question remained: why? I mean, I had those drivers with the stock kernel, so why weren't they built when I compiled the new kernel?



All this to ask: are ALSA and wireless drivers provided by some other package? Like some alsa-driver and iwl3945-driver (which don't exist by there names, BTW)?

---

### Post by sdennie on 2008-06-14
I've seen the same thing when building a custom kernel and using an Ubuntu kernel config as the base.  My guess is that it's important enough to have up to date alsa and wifi drivers that they build them outside the source tree and just include those modules in the kernel.  In fact, you can do the exact same thing without having to rebuild the kernel if you want.

---

### Post by pedrogfrancisco on 2008-06-15
Ya but I thought there'd be a separate package then.

I just rebuilt my kernel because my laptop's suspend was faulty (though now it seems to be working fine with the stock kernel, go figure).

Anyway, thanks for the reply :) I was trying to find out if ALSA and Wireless were provided by some other package and by adding them in the kernel .config I'd be messing things up, but according to what you said, seems it's not the case.

Thanks :)

---

