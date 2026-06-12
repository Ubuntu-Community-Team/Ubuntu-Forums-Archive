---
title: "Problems while playback audio in Ubuntu Studio 19.10 with M Audio 1010LT"
date: 2020-02-13
forum: General Help
---

### Post by Fenixin on 2020-02-13
Hello there!

I'm having some problems with my home studio after updating to Ubuntu Studio.

A few months ago, my old motherboard died. I had to buy a new motherboard, new SSD and a lot of new stuff. When I tried to run the old KXstudio my new SSD wasn't even recognized.

So, I updated the system to Ubuntu Studio and since then I'm having background noise problems and clicks while playing high volume noises. The background noise increases when moving the mouse or moving big changing graphics in the different running programs.

The funny thing is that just booting a live CD of the old KXstudio solves all the issues, no background noise, and no clicks in the instruments, perfect sound.

And recently I have discovered that I can solve all the issues if I run a stress-ng command running one cpu at 100%. For as long as I have stress-ng running my audio rig works like a charm.

I've also tried to boot a AV Linux 2020 and the same issues are there.

All this make me think that there is some kind of problem the real time kernel or the energy management of the system.

Also! An external Focusrite 2i4 second Gen works with no problem in Ubuntu Studio.

Does anybody know what is going on? Is there anything I can try? Anywhere to ask for help? 

Thanks in advance


System Information:
Ubuntu Studio      18.04.3 LTS bionic (backports) Kernel~4.15.0-74-lowlatency

Sound Card:  M Audio 1010LT      ICE1712 multi (Envy24) PCI Multi-Channel I/O Controller
MotherBoard:  ASUSTeK COMPUTER INC.    PRIME B360-PLUS  with 2 PCI SLOT
Graphic Card:  Motherboard integrated    Intel Corporation Device 3e92

Processor:  Intel(R) Core(TM)     i5-8400 CPU @ 2.80GHz
Memory:    16GiB   Corsair    DIMM DDR4 synchronous 2400 MHz (0,4 ns)
BOOT Disk:  Samsung       970 EVO Plus 500GB SSD NVMe M.2

---

