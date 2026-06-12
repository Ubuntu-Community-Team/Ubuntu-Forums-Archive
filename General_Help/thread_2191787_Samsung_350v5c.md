---
title: "Samsung 350v5c"
date: 2013-12-04
forum: General Help
---

### Post by septekin on 2013-12-04
I made the mistake of buying my third Samsung laptop, not realizing that Windows 8 has made it all but impossible to install other operating systems. I managed to install and get operating my favourite Ubuntu 10.04.3. However I cannot get the sound working. Using the module-assistant, installed alsa but still no sound. The following is the relevant extract from lshw:

*-multimedia UNCLAIMED
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:c0210000-c0213fff

Can someone please tell me if I stand a chance of making the audio work?

The installed alsa module is: Version 1.0.22.1+dfag-0ubuntu3+2.6.32-53.115 of alsa-modules-2.6.32-53-generic.

---

### Post by Isamu715 on 2013-12-04
Ubuntu 10.04 is out of support on the desktop. Also, it's likely that since your PC came with Windows 8 pre-loaded your hardware is simply not supported by 10.04 as it uses an old version of the Linux kernel. I'd recommend switching to a newer version of Ubuntu.

---

### Post by septekin on 2013-12-05
Thanks a lot Isamu715. I was planning to remain with 10.04.4 LTS until the next year's LTS came out.
The latest disk I have is 13.04 (gratitude to the "Linux Magazine"). I installed it into a spare partition: both the Wi-Fi and the audio started without any hassle. Thanks again.
teoman

---

### Post by mörgæs on 2013-12-05
Good, please mark the thread 'solved'.

---

