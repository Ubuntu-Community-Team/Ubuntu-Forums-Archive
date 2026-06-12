---
title: "intel hda not working after suspend (8.04)"
date: 2008-04-25
forum: General Help
---

### Post by Käptn K on 2008-04-25
Hello fellow Ubuntuusers, 

Unfortunately my first post has to be a support request. 
I am running Ubuntu for almost 2 years now on my self build workstation, started with Edgy, went over to Feisty and then gutsy. 

I never had any problems with my hardware, as it is completely supported by intels open source division. I never had any problems with suspend to ram, suspend to disk or power on standby. Every component made a nice wakeup and ran perfectly. 

But with Hardy (32bit) I got a serious problem with my onboard soundchip. 
Here are workstations specs: 

mainboard: Aopen i945GMm-HL (i945GM Chipset), sound onboard Realtek 883 (uses intel_hda drivers), gfx onboard (GMA 950)
RAM: MDT CL4 2x1024 Mibibyte (runinng in dual channel mode)
CPU: Intel Core 2 Duo (Merom) T5500 1,66GHz
HD: Western Digital Caviar SE 160 Gigabyte 7200rpm 8mb cache

The machine goes into S3 perfectly, but the soundchip is completely deactivated after wakeup. There is no sound at all, using the volume-control in the gnome panel crashes X. 

lspci works nicely before S3, after wakeup it crashes the machine hard. 

There are no problems at all in Edgy, Feisty or Gutsy, just in Hardy Heron.

I searched the common Ubuntuforums, but aside the usual Pulse Audio problems I didnt find anything regarding this behaviour. 

Has anyone any idea what causes the failing soundchip and the hard crashes after S3?

Thanks in advance

Käptn K

---

