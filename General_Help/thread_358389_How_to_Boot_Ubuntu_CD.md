---
title: "How to Boot Ubuntu CD"
date: 2007-02-10
forum: General Help
---

### Post by Bartolo on 2007-02-10
I am unable to boot my 6.06 CD on my previous computer. The instructions on the CD sleeve say to place the CD in the drive and restart the computer. This does not work. Instead the old Win 98 system comes up.

The sleeve also says to install Ubuntu, to double click on the "Install" icon. I have no Install icon on the CD; rather an Install folder that contains only three files: a ReadMe, and two others that are not .exe files. Double clicking on either of those does not start an install process.

What should I do, either to run from the CD or install from the CD. I have no use for that old Win 98 system.

Thanks very much.

---

### Post by r4ik on 2007-02-10
Set you're boot order to cd-first.
Try Del or Esc to get into you're bios.

Good luck !

---

### Post by meng on 2007-02-10
What are the other two files? I wonder if you may have been the disc wrongly.

---

### Post by teaker1s on 2007-02-10
your issue is the motherboard bios will most likely not have cdrom boot support, check bios boot sequence options
 to boot you will need boot floppy that enables cd-rom support so you can boot the cd. Or a bios update may offer cdrom boot support

Secondly depending on your hardware you may find that a lighter distro will give you better performance

---

### Post by Bartolo on 2007-02-10
Thanks, R4iK. I needed to change the boot order in BIOS as you said.

Running from the CD on my old 500MHZ machine was very slow - 10 minutes to boot,
and so on. I guess I need to install the program, no?

And then I need a user guide. Is there a generally recommended UG for beginners, or 
is that a question with a hundred answers?

Bartolo

---

### Post by meng on 2007-02-10
If you can tell us how much RAM you have, we can advise the best distro to install. You may not have enough to install from that CD, for example, but there are other CDs and other distros.

---

### Post by Bartolo on 2007-02-10
Meng, I have not *installed* Ubuntu yet, I was running from the CD. It has been
years since I added memory to that machine but as I recall I have 374K of RAM.

---

### Post by meng on 2007-02-10
374 KB? Are you sure you don't mean 374 MB, or even 384 MB? Well I assume you mean MB. And theoretically, you should have enough to boot AND install from the Live CD. But sometimes hardware incompatibilities get in the way and you may need to use the Alternate CD instead. But that will only give you the option to install, not to run the live desktop without installing.

---

