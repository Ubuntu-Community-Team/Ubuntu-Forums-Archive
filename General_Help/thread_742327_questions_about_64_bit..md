---
title: "questions about 64 bit."
date: 2008-04-01
forum: General Help
---

### Post by Raccoon1400 on 2008-04-01
I want to upgrade to the 64 bit ubuntu. My processor is a core 2 Duo, 1.6GHz
I have a few questions.

Are there different repos for 64 bit? If so, are they the same/ almost the same?
In other words, I want to make sure I can get all my programs for 64 bit.

Can I still run 32 bit windows programs in WINE?

Can I run 32 bit OS in Virtual Box if I upgrade to 64 bit?
Can I try out 64 bit in virtual box over a 32 bit system?

Will boot times be significantly less?(currently about a minute.

---

### Post by Slushdoot on 2008-04-01
[list=1][*]Yes, there are different repos for 64-bit.  99.9% of the packages they contain are the same as the 32-bit ones, just compiled for the AMD64 architecture instead of i386.  Others are not the same, particularly proprietary things like the Mozilla Flash plugin and restricted codecs.  The devs have made it easy to use the 32-bit versions of these applications in some cases.  Try out the 64-bit livecd and see what you can install.[*]No, I don't think that they can since the libraries Wine uses are specific to 32-bit operation.  I could be wrong on this. ;)[*]I don't know about Virtualbox, but I've done it in VMware workstation without issue.[*]Boot times will probably be identical since it's largely determined by the speed of the hard disk and the number of things it has to load.[/list]

---

### Post by Raccoon1400 on 2008-04-01
> No, I don't think that they can since the libraries Wine uses are specific to 32-bit operation. I could be wrong on this.

Do you mean wine can't run at all, or just can't run 64 bit programs?

---

### Post by Raccoon1400 on 2008-04-01
> Boot times will probably be identical since it's largely determined by the speed of the hard disk and the number of things it has to load.

wouldn't the  speed they could be loaded be affected by a processor?

---

### Post by Slushdoot on 2008-04-01
Wikipedia says:> Wine cannot currently run 64-bit Windows applications; however, it can run on 64-bit operating systems. Since almost all Windows applications are currently available in 32-bit versions, support for 64-bit Windows applications is a low priority, planned for after version 1.0.

On a 64-bit Linux system, support for 32-bit Windows applications is handled by linking with 32-bit versions of Wine's shared library dependencies.So it would appear that I was wrong.

Booting is, for the most part, bound by I/O.  A faster processor can issue I/O requests faster but still has to wait for the disk to get the requested bits.  Either way, 64-bit operation is barely noticably faster than 32-bit operation on the desktop.  I don't think you'd be able to tell the difference in boot time.

---

