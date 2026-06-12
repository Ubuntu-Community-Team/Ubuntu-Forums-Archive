---
title: "stacking at 33% :("
date: 2007-05-19
forum: General Help
---

### Post by ooblez on 2007-05-19
all goes well up until i get to formatting the virtual disks at 33%

so i did as the FAQ asked and typed in hdparm -I /dev/sda but this just brings up crap mainly about security :(

no sign of UDMA modes: udma0 udma1 udma2 udma3 udma4 '''*udma5'''

I'm running a Fujitsu Siemens Amilo A if that helps:)

thanks very much, im looking forwards to being able to use Ubuntu:D

EDIT: forgot to mention that before rebooting i created my own virtual disk as suggested via fsutil file createnew C:\wubi\disks\system.virtual.disk 4000000000

and i left it at the default sizes which I believe are all below 4gb :D (EDIT: apparently not, I'll try a reinstall)

EDIT: and I left it for a good 5 hours:P

I'd ask you guys to fix this please:) As a web designer and php coder I need a bit more than 4gb space:P

keep up the great work:D

---

### Post by ago on 2007-05-21
> **ooblez said:**
> 
I'm running a Fujitsu Siemens Amilo A if that helps:)


Yep that helps. Foxtrott, also reported the same problem and he also is using a Fujitsu Siemens Amilo...

---

### Post by Cloudedbrains on 2007-05-23
I had to reduce the size of the virtual drive and host (I think) in the "Advanced formatting" options then my install went well :)

---

