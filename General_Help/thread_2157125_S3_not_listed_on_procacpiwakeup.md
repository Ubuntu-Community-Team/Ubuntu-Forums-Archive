---
title: "S3 not listed on /proc/acpi/wakeup"
date: 2013-06-24
forum: General Help
---

### Post by roudy1989 on 2013-06-24
Hello,

I want my laptop to resume from S3 (suspend to ram) when I open the lid. It suspends without any problems when closing the lid.
I noticed that there is no S3 listed in /proc/acpi/wakeup. Only S4. Here is the output of cat /proc/acpi/wakeup:
```
Device    S-state      Status   Sysfs nodeP0P1      S4    *disabled
GLAN      S4    *disabled
EHC1      S4    *enabled   pci:0000:00:1d.0
EHC2      S4    *enabled   pci:0000:00:1a.0
HDEF      S4    *disabled  pci:0000:00:1b.0
RP01      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *disabled  pci:0000:02:00.0
RP02      S4    *disabled
PXSX      S4    *disabled
RP03      S4    *disabled
PXSX      S4    *disabled
RP04      S4    *disabled  pci:0000:00:1c.3
PXSX      S4    *enabled   pci:0000:03:00.0
RP05      S4    *disabled  pci:0000:00:1c.4
PXSX      S4    *enabled   pci:0000:04:00.0
RP06      S4    *disabled
PXSX      S4    *disabled
RP07      S4    *disabled
PXSX      S4    *disabled
RP08      S4    *disabled
PXSX      S4    *disabled
PEG0      S4    *disabled  pci:0000:00:01.0
PEGP      S4    *disabled  pci:0000:01:00.0
PEGA      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
PWRB      S4    *disabled
```

Trying to enable all disabled items does not change anything. I think I have to make S3 things to be listed first.
So, now my specs:
I've got an Samsung Series 7 Chronos 700Z3A-S02DE. It's a normal BIOS, that is updated to the newest version.
If there are any questions for more information please ask. I really appreciate your help. Thank you.

---

### Post by gordintoronto on 2013-06-24
What version of Linux?

With my HP G62 laptop, I close the lid, it suspends, I open the lid it resumes. I've never had to worry about the stuff you are looking at.

My /proc/acpi/wakeup, Ubuntu 13.04:
Device	S-state	  Status   Sysfs node
PB2	  S5	*disabled
PB3	  S4	*disabled
PB5	  S5	*disabled  pci:0000:00:05.0
PB6	  S4	*disabled  pci:0000:00:06.0
USB0	  S3	*enabled   pci:0000:00:12.0
USB1	  S3	*enabled   pci:0000:00:13.0
USB4	  S3	*enabled   pci:0000:00:12.2
USB5	  S3	*enabled   pci:0000:00:13.2
USB6	  S3	*enabled   pci:0000:00:16.2
PS2K	  S3	*enabled   pnp:00:06
PS2M	  S3	*disabled  pnp:00:07
P2P	  S5	*disabled  pci:0000:00:14.4

---

### Post by roudy1989 on 2013-06-24
I use a fully upgraded Ubuntu 13.04.

laze@devlet:~$ uname -a
Linux devlet 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I found this [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1060471](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1060471) launchpad bug report. As it seems, it are only Samsung laptops, that make trouble (in this special bug report).
They also suffer from the same problem and their acpi wakeup tables show only S4, too.

---

