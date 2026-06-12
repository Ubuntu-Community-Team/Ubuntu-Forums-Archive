---
title: "IA-64 intel pentium processor &quot;Itanium&quot;"
date: 2016-01-05
forum: General Help
---

### Post by ethan30 on 2016-01-05
I need to know which of these types of processor installers are compatible with my processor.
AMD64
ARM64
ARMEL
ARMHF
I386
MIPS
MIPSEL
POWERPC
PPC64EL
S390X
I have VMWare Workstation Player and was hoping to install Debian to it to try it out, but I am not sure which of the image installer types to download since my processor is not listed in the provided installer types.

---

### Post by grahammechanical on 2016-01-05
The clue is in "-64." It is a 64 bit CPU. To confirm it,

[https://en.wikipedia.org/wiki/IA-64](https://en.wikipedia.org/wiki/IA-64)

In theory AMD64 or i386 should run on this chip. In theory.

AMD64 is for 64 bit CPUs built by both Intel & AMD. i386 is for 32 bit CPUs built by both Intel & AMD. A 32 bit OS should run on both 32 bit CPUs and 64 bit CPUs as the 64 bit architecture is backwards compatible with 32 bit operating systems. How much this applies to the IA-64 CPU I do not know. In fact I have just found this

> *Please note that the ia64 architecture is for Intel Itanium  Processors Only. (Intel's "ia64" architecture is different. Ubuntu  doesn't officially support ia64 yet, but work is well underway, and many  Ubuntu/ia64 packages are available as of 2004-01-16).*

[https://help.ubuntu.com/community/SupportedArchitectures](https://help.ubuntu.com/community/SupportedArchitectures)

MY advice would be to download the AMD64 ISO image and burn it to disk/USB stick and try to run a live session. There you will find out from practical experience if the standard 64 bit Ubuntu OS run on the IA-64 CPU architecture. It is certain that Ubuntu does not produce an ISO image specially for the IA-64.
> 
Itanium is supported by the following [operating systems]("https://en.wikipedia.org/wiki/Operating_system"):

 
[LIST]
[*][HP-UX]("https://en.wikipedia.org/wiki/HP-UX") 11i
[*][OpenVMS]("https://en.wikipedia.org/wiki/OpenVMS") I64
[*][NonStop]("https://en.wikipedia.org/wiki/NonStop") OS, an [Intel 64]("https://en.wikipedia.org/wiki/Intel_64") (x86-64) port is being developed.
[*][GNU/Linux distributions]("https://en.wikipedia.org/wiki/GNU/Linux_distributions") (including [Debian]("https://en.wikipedia.org/wiki/Debian"), [Gentoo]("https://en.wikipedia.org/wiki/Gentoo_Linux") and [SUSE's SLE]("https://en.wikipedia.org/wiki/SUSE_Linux_distributions"))
[*][FreeBSD]("https://en.wikipedia.org/wiki/FreeBSD")[SUP][[37]]("https://en.wikipedia.org/wiki/IA-64#cite_note-37")[/SUP]
[*][Bull GCOS]("https://en.wikipedia.org/wiki/General_Comprehensive_Operating_System") 8
[/LIST]


> [Canonical]("https://en.wikipedia.org/wiki/Canonical_Ltd")'s [Ubuntu 10.04 LTS]("https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_10.04_LTS_.28Lucid_Lynx.29") (released in April 2010) was the last supported Ubuntu release on Itanium

[https://en.wikipedia.org/wiki/IA-64](https://en.wikipedia.org/wiki/IA-64)

Regards.

---

### Post by Yellow Pasque on 2016-01-05
> **grahammechanical said:**
> In theory AMD64 or i386 should run on this chip. In theory.

No, they won't run on the Itanium itself. IIRC, some Itaniums could run some x86 apps through emulation, but I doubt they would run an entire x86 OS.

> I need to know which of these types of processor installers are compatible with my processor.
None of them in the list are what you need (IA-64) for native CPU support. Debian 7.x was the last release to support IA-64.

I don't know enough about VMWare to say whether you can virtualize x86 or x86-64 (aka amd64) on an Itanium. I would guess so, but then googling the matter shows that VMWare lists the Itanium as completely unsupported by VMWare Workstation.
*Shrug*

---

