---
title: "Backup Ubuntu installed with Wubi"
date: 2007-06-17
forum: General Help
---

### Post by alegeott on 2007-06-17
Hi, i am a newbe, sorry if this post isn't intelligent and for my bad english :D...
All right, my question: is possible to make a ubuntu's backup installed with Wubi?
I have installed my system with Wubi because all other attempt of install with ubuntu and other distro are freezeng during the process.
The problem could be the interaction between the new sata HDD (seagate ST3320620AS) and the nforce430 chipset, the ati video card, a bad support for MY amd64x2 cpu or my RAM memory...
With Wubi, instead, all right. But i need to make a backup, because i would install the ati 3D driver and the first attempt isn't good (black screen instead of login page).

My hardware configuration:
mb A8N-VM CSM,
cpu amd 939 4200+ x2 core Manchester
2x512mb pc3200 ddr400 [KVR400X64C3A/512]
video card Peak x1950gt 256bit 256mb ddr3
HDD IDE maxtor 6E030L0, IDE 1° master (windows)
HDD sata seagate ST3320620AS (storage data)
HDD quantum Fireball 20Gb, IDE 1° slave (Ubuntu-Wubi)
burner nec 3550A@4551, IDE 2° master
dvd-rom PIONEER DVD-114, IDE  2° slave
wireless card Linksys WUSB54G v.4
APC BAck UPS CS 500 (500w)
power supply LC6550GP v2 (550w)

Note: i can't install on the sata HDD: the boot is blocked after the first line of menu.lst. This bug is known?
@ago: Are you italian?

---

### Post by ago on 2007-06-17
> **alegeott said:**
> Hi, i am a newbe, sorry if this post isn't intelligent and for my bad english :D...
All right, my question: is possible to make a ubuntu's backup installed with Wubi?
Just copy the c:\wubi\disks somewhere else

> Note: i can't install on the sata HDD: the boot is blocked after the first line of menu.lst. This bug is known?
Try the latest minefield: [http://www.cutlersoftware.com/ubuntusetup/minefield.html](http://www.cutlersoftware.com/ubuntusetup/minefield.html)

> @ago: Are you italian?
Si

---

