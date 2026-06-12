---
title: "No sound after upgrade from 20.04 to 20.10!"
date: 2020-10-24
forum: General Help
---

### Post by chj85 on 2020-10-24
Hi there.
There's no sound after I upgraded from 20.04 to 20.10.
I tried uninstalling and reinstalling alsa and pulse (sudo apt remove --purge alsa-base pulseaudio && sudo apt install alsa-base pulseaudio), then I did "sudo alsa force-reload" but with no luck.
I installed inxi to see if it could detect my hardware. I did "inxi -SMA", which gave me;
[B]System:
  Host: Chris Kernel: 5.8.16-xanmod1 x86_64 bits: 64 
  Desktop: KDE Plasma 5.19.5 Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:
  Type: Laptop System: Micro-Star product: GE63 Raider RGB 8RE v: REV:1.0 
  serial: <superuser/root required> 
  Mobo: Micro-Star model: MS-16P5 v: REV:1.0 serial: <superuser/root required> 
  UEFI: American Megatrends v: E16P5IMS.101 date: 02/26/2018 
Audio:
  Device-1: Intel Cannon Lake PCH cAVS driver: snd_hda_intel 
  Device-2: NVIDIA GP106 High Definition Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.8.16-xanmod1 

So obviously it was detected.
This is really weird.
Any idea? Please help.
Thanks in advance![/B]

---

### Post by chj85 on 2020-10-24
Solved on my own.
The generic kernel failed on me so I tried the xanmod kernel which wouldn't work either, so then I installed the Liqourix kernel.
This worked like a charm.
I know it's not an ideal fix. But if any of you guys run into this problem, then there you go! &#128512;

---

