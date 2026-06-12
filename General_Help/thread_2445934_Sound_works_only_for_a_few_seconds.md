---
title: "Sound works only for a few seconds"
date: 2020-06-22
forum: General Help
---

### Post by koma77 on 2020-06-22
I have an ASUS Zenbook and since I upgraded to 20.04 the sound output has become shaky.

Often it only works for a couple of seconds, then it is silent. I can't hear sound even if I use the sound setting and click on "test speakers".

I dual boot Windows, and there the sound works fine, so it is not a HW issue.

The sound HW is:
  *-multimedia
       description: Audio device
       product: Sunrise Point-LP HD Audio
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:130 memory:ef228000-ef22bfff memory:ef200000-ef20ffff

Neither the kernel log nor the syslog shows anything exciting when this problem happens.


Does anyone recognize this problem or have any idea what I can test?

---

### Post by gdesilva on 2020-06-23
Have you seen this post?

[https://www.linux.org/threads/asus-zenbook-15-ux534f-realtek-hd-audio-problem.27384/](https://www.linux.org/threads/asus-zenbook-15-ux534f-realtek-hd-audio-problem.27384/)

Hope this will be of use.

---

