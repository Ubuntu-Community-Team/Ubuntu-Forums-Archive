---
title: "ubuntu 14.04 display does not initiate on boot"
date: 2015-02-04
forum: General Help
---

### Post by Derelinquat fenestras on 2015-02-04
Hello all!  I need some help with my Asus x200m laptop running ubuntu 14.04 64bit.  I was using it last night with no problems and I closed the lid and put it away.  When I opened the lid this morning, and the screen was blank and none of the status lights were on.  I hit the power button and it appeared as though it was stating properly until I never saw the ubuntu splash screen.

By the way, I believe the kernel updated yesterday.
All of the status lights come on (battery, screen, wifi, hard drive) and when the hard drive stops doing anything, I can type my password in and I can tell the system loads.  I use synapse launcher and am able to ctrl+space and type shut down and it shuts down.  
I know that the screen itself is not broken/disconnected because I can get the bios menu to open and everything works fine.
now I trI'd to access my grub menu so that maybe I could just run an older version of the kernel, but I hold shift and nothing happens.
does anyone know if there is a command line way to force the display on, revert to previous kernel, or have any other ideas.

Thank you all in advance

**by the way, I realize that u could probably use a USB live ubuntu to fix the problem, but I'm at work and require the use of my computer so I was wondering during if there was any other way.**

---

### Post by Derelinquat fenestras on 2015-02-05
Hello again!
Not sure if anyone will read this, but I was able to fix the problem by plugging my computer int an external monitor and installing a very useful program called grub-customizer.  Installation instructions below...

Still not sure why my GRUB would no load when I held shift, but I was able to check the box on the grub-customizer GUI under General Settings Tab > Menu Visibility > show menu.
Now grub always loads when I turn my computer on.

If anyone does have any ideas as to why this all went down, I'd love to hear them!

Thanks again!

INSTRUCTIONS TO INSTALL GRUB-CUSTOMIZER

>in terminal

sudo add-apt-repository ppa:danielrichter2007/grub-customizer

sudo apt-get update

sudo apt-get install grub-customizer

---

