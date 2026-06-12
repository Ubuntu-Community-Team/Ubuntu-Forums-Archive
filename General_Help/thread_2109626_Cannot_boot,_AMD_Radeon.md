---
title: "Cannot boot, AMD Radeon"
date: 2013-01-28
forum: General Help
---

### Post by Mutinize on 2013-01-28
I've installed my OS countless times because of this problem and I can't figure out how to fix it. Whenever I boot to ubuntu my screen with either flicker purple until it just freezes, stays completely black, or sometimes if I'm lucky it'll boot without a problem. I've lurked lots of threads with people with remotely close issues saying to install the latest AMD Catalyst beta drivers (gives me an error about fglrx) and/or update my kernel to 3.8 (which gets me screen resolution stuck at ~640x480, never fails to boot however). Does anyone know how to fix this? I've considered installing mint or fedora but if it's because of the kernel then I'll have the same problem, correct?

AMD E-300 APU with Radeon(tm) HD Graphics 
Ubuntu x64 / Windows 7 Ultimate x64

---

### Post by Mutinize on 2013-01-28
Sorry to bump but I don't know how to fix this. Anyone? Please?

---

### Post by E411 on 2013-01-29
Hi there,

I don't know much but I had a similar problem and although I only solved it by reinstalling I got some really good advice in that thread: [http://ubuntuforums.org/showthread.php?t=2107354](http://ubuntuforums.org/showthread.php?t=2107354)

Before the gurus come and have a look on your problem, here are some usefull things to know:

- to figure out what hardware and modules you're on:

```
sudo lshw -C display
lspci -nnk | grep -iA3 vga
```- to try to force a boot with kernel options:

access grub at boot holding the shift key 
cursor on top item (latest kernel), hit 'e' for edit and insert 'nomodeset' before 'quiet splash' then F10
once in, you can reset unity, try to startx, have a look on your x config files, ...

Then post the info you managed to gather and wait for a guru...

---

