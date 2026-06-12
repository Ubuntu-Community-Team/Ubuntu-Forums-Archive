---
title: "Problems watching Youtube videos with Ubuntu 24.04"
date: 2024-07-03
forum: General Help
---

### Post by Joe_Linux on 2024-07-03
I installed Ubuntu 24.04 on a Asus Chromebook C300s (that was at it's end of it's support by Google in 2022) using Mrchromebox. My concern is this when watching a Youtube video it is normal for awhile then I get the circle showing it is buffering and a tone (the tone is not affected by the volume control). This is what I did on the command line
```
lspci
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 35)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 35)
00:10.0 SD Host controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series MMC Controller (rev 35)
00:12.0 SD Host controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SD Controller (rev 35)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 35)
00:1b.0 Audio device: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller (rev 35)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 35)
00:1c.2 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #3 (rev 35)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 35)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
```
also ```
mark-grisham@mark-grisham-Terra:~/Desktop$ sudo lshw -C network
[sudo] password for mark-grisham: 
  *-network                 
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 59
       serial: 88:78:73:69:7d:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=6.8.0-31-generic firmware=29.4063824552.0 7265D-29.ucode ip=192.168.1.70 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:313 memory:91200000-91201fff
```
       I tried this in Firefox and Chromium with similar results (a similar tone after the video played for awhile) have not experienced the problem elsewhere.
       Thanks for any help

---

### Post by currentshaft on 2024-07-03
What is a "tone"? Surely you must realize how vague and confusing that must sound to readers not experiencing your problem?

---

### Post by Joe_Linux on 2024-07-03
> **currentshaft said:**
> What is a "tone"? Surely you must realize how vague and confusing that must sound to readers not experiencing your problem?

Sorry for not being descriptive enough. The tone is somewhat high pitched and I get the partial circle showing a buffering problem.

---

### Post by currentshaft on 2024-07-04
> **Joe_Linux said:**
> Sorry for not being descriptive enough. The tone is somewhat high pitched and I get the partial circle showing a buffering problem.

Like a whistle? Never heard of something so strange. Have you installed any browser extensions? Can you try to reproduce the issue on other video sites?

---

### Post by TenPlus1 on 2024-07-07
The tone sounds like cable interference from your speakers maybe, I get this sometimes from my really cheap Trust speakers because the cables arent shielded.

As for YouTube, the best way to help improve it's performance in Firefox is to use uBlock Origins and enable the Annoyance filters, also when playing the video turn off Ambient mode in the settings cog :)

---

