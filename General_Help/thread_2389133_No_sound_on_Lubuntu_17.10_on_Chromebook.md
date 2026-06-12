---
title: "No sound on Lubuntu 17.10 on Chromebook"
date: 2018-04-12
forum: General Help
---

### Post by darthkelly on 2018-04-12
Hello all,

I recently installed Lubuntu 17.10 on my ASUS Chromebook Flip C302. All seems to be going well (other than some issues with Stata which took forever to resolve), except the sound does not appear to be working. Sound works fine on ChromeOS. The sound is not working for either the on-board speakers or my headphones when plugged into the audio jack (my bluetooth headphones have dead batteries, otherwise I'd try to replicate with them as well. I tried running pavucontrol, but did not see any options that would help. I saw in similar thread to post lspci results, so here they go:

```
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)00:02.0 VGA compatible controller: Intel Corporation HD Graphics 515 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:19.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #2 (rev 21)
00:19.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #4 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1e.4 SD Host controller: Intel Corporation Device 9d2b (rev 21)
00:1e.6 SD Host controller: Intel Corporation Sunrise Point-LP Secure Digital IO Controller (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 9d46 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Multimedia audio controller: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.5 Non-VGA unclassified device: Intel Corporation Device 9d24 (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)



```

Any help will be greatly appreciated!!

---

### Post by Yellow Pasque on 2018-04-14
[https://github.com/GalliumOS/galliumos-distro/issues/379](https://github.com/GalliumOS/galliumos-distro/issues/379)

---

### Post by darthkelly on 2018-07-28
> **Temüjin said:**
> [https://github.com/GalliumOS/galliumos-distro/issues/379](https://github.com/GalliumOS/galliumos-distro/issues/379)

Thank you for your reply. I am running Lubuntu, and those commands look like they are for Gallium repositories. Will this fix still work?

---

### Post by Impavidus on 2018-07-29
You took your time to reply...

I don't know about your issue, but did you notice that Lubuntu 17.10 reached end of live 10 days ago? The newer kernel on 18.04 may help.

---

