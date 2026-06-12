---
title: "TTY either blank or non-functional?"
date: 2016-05-02
forum: General Help
---

### Post by neu5eeCh on 2016-05-02
Using Kubuntu 16.04.

Kernel: 4.4.0-21-generic x86_64 (64 bit) Desktop: KDE Plasma 5.5.5
           Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 20428 v: Lenovo Yoga 2 11
           Mobo: LENOVO model: VIUU4 v: 31900058WIN Bios: LENOVO v: AACN21WW date: 01/30/2015
CPU:       Dual core Intel Core i3-4012Y (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 1500 MHz 1: 1500 MHz 2: 1498 MHz 3: 1500 MHz 4: 1495 MHz
Graphics:  Card: Intel Device 0a1e
           Display Server: X.Org 1.18.3 driver: intel Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Haswell GLX Version: 3.0 Mesa 11.2.0

Am noticing that when I switch to TTY 1-6, I get a prompt but no cursor or ability to interact with the prompt -- as if TTY were locked up? Is this a known bug?

---

### Post by neu5eeCh on 2016-05-04
Okay, I may have found a workaround that might also have fixed the "missing glyphs/letters" --- switching back to an older kernel.

Based on this information:

[http://askubuntu.com/questions/688306/text-missing-garbled-after-laptop-resumes-from-sleep-mode](http://askubuntu.com/questions/688306/text-missing-garbled-after-laptop-resumes-from-sleep-mode)

[http://www.spinics.net/lists/intel-gfx/msg82135.html](http://www.spinics.net/lists/intel-gfx/msg82135.html)

Used "[Grub Customizer]("https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer")" 'cause it's easy. Instead of 4.4, am now using 4.2.0-25-generic x86_64 (64 bit).

---

