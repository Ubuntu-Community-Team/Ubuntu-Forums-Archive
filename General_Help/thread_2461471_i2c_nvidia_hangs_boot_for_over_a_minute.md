---
title: "i2c nvidia hangs boot for over a minute"
date: 2021-05-01
forum: General Help
---

### Post by vidtek on 2021-05-01
See attached picture of boot screen.

This bug is discussed on askubuntu here:[https://askubuntu.com/questions/1278399/dual-system-ubuntu-20-04nvidia-gpu-i2c-timeout-error-ucsi-ccg-i2c-transfer]("https://askubuntu.com/questions/1278399/dual-system-ubuntu-20-04nvidia-gpu-i2c-timeout-error-ucsi-ccg-i2c-transfer")

The solutions proffered are drastic and not simple.  Has anyone any simple fix for this?

Cheers, Tony

EDIT:  see post #3  red herring

---

### Post by CelticWarrior on 2021-05-01
#2 doesn't seem drastic or too complex:

> [COLOR=#242729][FONT=inherit]You may want to create a file [/FONT][/COLOR]/etc/modprobe.d/blacklist_i2c-nvidia-gpu.conf[COLOR=#242729][FONT=inherit] with these contents: [/FONT][/COLOR]blacklist i2c_nvidia_gpu[COLOR=#242729][FONT=inherit]. This file prevents loading the problematic driver.[/FONT][/COLOR]&#8203;

---

### Post by vidtek on 2021-05-02
> **CelticWarrior said:**
> #2 doesn't seem drastic or too complex:

This old fart stuffed it up again.....I did some more digging and the nvidia thing was a red herring.

The actual problem turns out to be my second nvme drive a Sabrent 2tb.  fsck is taking forever on this new drive every boot.  

As a temporary measure I disabled fsck on boot in my grub configuration, not an ideal thing.  I have created a support ticket on the sabrent site, let's hope they can 

sort it out for me.

Apologies to all, Tony.

---

