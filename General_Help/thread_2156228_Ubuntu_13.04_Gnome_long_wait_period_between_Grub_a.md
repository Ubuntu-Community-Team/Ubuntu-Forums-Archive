---
title: "Ubuntu 13.04 Gnome: long wait period between Grub and boot"
date: 2013-06-21
forum: General Help
---

### Post by nine9nine on 2013-06-21
Hi guys, I have Ubuntu 13.04 Gnome installed on my laptop (dual booting with Windows 7), and I've been having an issue that I've had with previous versions of Ubuntu.  After I select Ubuntu from the Grub menu, I'm left at a blue screen (the background color for Grub) for a good 10 seconds or so until Ubuntu starts to boot.  For me, it shows this blue screen, then finally shows some line of code on a black screen for a second, then is right at the login screen.  This similar thing has happened for me with previous versions: I'd wait at a screen the same color as the Grub background, get the Ubuntu boot screen with the dots for a second, and then be right at the login screen.  However, when I go to boot Windows, it goes straight from Grub to the Windows boot animation.  What I'm wondering is why does booting into Ubuntu cause this delay between Grub and the start of the boot sequence?  It doesn't seem like this screen is a part of the actual OS boot.

---

### Post by carl4926 on 2013-06-21
This sounds fairly normal

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by nine9nine on 2013-06-21
Ok, thanks.  I've seen multiple posts around the internet about this, none with any real answer, so I was just curious.

---

### Post by grahammechanical on 2013-06-21
The Windows operating system has the advantage of being developed by one company that has the money to hire many developers and also have the influence to get technical details from hardware makers.

A Linux distribution is made up of many components that are developed by small groups of developers independently and often as volunteers. Ubuntu is supported by a company called Canonical but it is not a wealthy company and it has to employ people to make money and not just develop the Ubuntu distribution. So, there is still a lot of community development.

And yet Canonical is working on a display driver called MIR and one of the benefits that it is hoped that MIR will bring is doing away with the handing over from one display server to another during the boot process. I count at least four as I watch the boot go from Grub to Login screen. And it is this handover that you are seeing. It is at the handover points that the boot process sometimes breaks down. As is happening to me running Saucy Salamander at this moment.

Regards.

---

