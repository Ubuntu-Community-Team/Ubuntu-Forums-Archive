---
title: "Can't seem to be able to install latest ubuntu flavours?"
date: 2013-08-03
forum: General Help
---

### Post by xyeovillian on 2013-08-03
I seem to be having problems with the latest ubuntu flavours I can't get any of them to load like its a graphic card problem.

Tried xubuntu 13.04,linux lite 1.0 Amethyst,Lubuntu 13.04 and Peppermint 4 and the screen goes blank after trying the live cd.

I have tried them on 3 Desktop PC's

1. AMD Athlon (tm) XP 2400+ 2.00 GHz Installed memory 2.00 GB

2.  HP - Compaq Pavilion 461.uk Desktop/PC Pentium 4 1.60 GHz 1.59 GHz 192 MB RAM

3. Intel Pentium 4 CPU 2.40 GHz Installed memory 992 MB

I have run earlier versions of Ubuntu on these computers and they have worked. I have thought Lubuntu Peppermint etc was suitable for older PC's

Is there some command that I need when loading CD/DVD's on start up.

---

### Post by TheFu on 2013-08-03
These are all very old systems. New Ubuntu releases require PAE support from the CPU by default.  You'll need to download the alternate install DVD and be certain to select a non-PAE version to be installed.  Learn more about this here: [https://en.wikipedia.org/wiki/Physical_Address_Extension](https://en.wikipedia.org/wiki/Physical_Address_Extension)


I'd also suggest that the HP computer not be used with any Ubuntu - you'd be better using TinyCore or DSL or Puppy Linux on that machine.  192MB just isn't enough RAM for any version of Ubuntu to run.

---

### Post by Bashing-om on 2013-08-03
xyeovillian; Hi !

I find it hard to believe that three systems will not boot any flavor of linux .... I would question the methology.
1. Have you checked the md5sum of the downloaded .iso(s) ?
2. Have you verified the burned as image disk's integrity (boot menu option on liveDVD) ?
3. Are you setting the bios boot priority to that of the drive as the 1st priority ?

If all the above is true one should boot to something. When booting up the liveDVD of ubuntu, hold the shift key at the purple splash screen .. do you now see the boot options menu ? Then measures may be taken to boot the operating system.

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

