---
title: "Can See Wireless Network But Can't Connect"
date: 2008-06-07
forum: General Help
---

### Post by Exsecrabilus on 2008-06-07
I'm running Ubuntu 8.04 i386.

I have a Broadcom B4318 wireless card built into my laptop.

I installed *b43-fwcutter* by the downloaded .deb file, and CDed (in Terminal) to the place where I pre-downloaded the *broadcom-wl-4.80.53.0.tar.bz2* file and the *wl_apsta-3.130.20.0.o* file.
Finally, I did the following:
```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```
I clicked the button for my wireless card and the light turned on.
It saw my wireless network point, but no matter how many times I click it, it won't connect!

What's wrong? (I'm writing this on my sister's MacBook, so note that I DON'T have Internet on the Ubuntu-installed laptop.) Thanks.

P.S. Just tried exact same thing on the Live CD I installed Ubuntu with, and it doesn't work there either. :(

---

### Post by Prospero2006 on 2008-06-08
Go to your linux box and type this:
```

sudo iwlist scan

```

Please print the output

---

