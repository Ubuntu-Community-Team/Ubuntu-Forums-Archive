---
title: "Disk problem /dev/hda"
date: 2007-10-14
forum: General Help
---

### Post by avram on 2007-10-14
hi everyone..

i recently reinstalled ubuntu again and i've had so many boot problems and software problems with stuff like applications closing themselves. 

i was advised to fdisk so i put into terminal fdisk /dev/hda/

and my result is..
The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

anyone know where i should go from here?

thanks...

---

### Post by geirha on 2007-10-14
Without knowing the problems you refer to, it's hard to give you any advice. Some more detailed explanation of the boot problems would help.

---

### Post by avram on 2007-10-23
hi again..

One of the first problems I just came across was when the loading screen came up with 'Ubuntu' above it, it did not load. The orange bar just stayed at the beginning, when it works it usually takes 5 seconds.

I tried starting my laptop again and it came up with this ...

640 K system RAM Passed
894M Extended RAM Passed
512 kb L2 Cache
system BIOS Shadowed
video BIOS shadowed
Fixed Disk 0: TOSHIBA MK1234GAX
Mouse initialized
ERROR
0200: Failure Fixed Disk 0

Press f1 to resume and f2 to go to setup


It is weird cause sometimes the computer decides to work, sometimes on start up it fails and soemtimes it works...

anyoen know what i should do?

---

### Post by geirha on 2007-10-23
That looks like the BIOS giving you that message. If the BIOS detects problems with the disk, then either it's not connected properly (a plug not completely plugged in perhaps), or your harddisk is crashing.

---

