---
title: "Ubuntu 7.04 LiveCD freezes on boot menu"
date: 2007-08-21
forum: General Help
---

### Post by kedmond on 2007-08-21
I have a Dell Dimension 3000.  It has 1 gig of RAM and an 80 gig hard disk.  I am running Windows XP on it.

I burned the Ubuntu 7.04 LiveCD as the web site instructs.  It was burned using a CentOS machine.

I cannot boot my computer from the LiveCD.  The Ubuntu menu shows up quickly, and then I can select the Memory Test option, or boot from the first disk option.  Both work fine.  If I select any of the other options, the computer freezes.  The word "Loading" appears at the top of the screen in green text, but it's also printed in a sort of jaggedy way to the far left.  And the menu seems to freeze at this point indefinitely.  There's no command line, or error window, or anything.  I can reboot by pressing "Control-Alt Delete".  That reboots just fine.

I'm not sure how to make this work.  Thanks.

-kedmond

---

### Post by jnorthr on 2007-08-21
You know, this sounds like you are being presented with the grub boot loader. This is a module that should only be available AFTER you install ubuntu. Here is a link to the grub documentation [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) for version 0.97 of supergrub. It will give you a flavor of what you may be seeing.

Have you ever tried to install ubuntu before and it failed ?
Can you currently use the windows o/s ?

When you reboot your machine from the live distro CD, do you see any menus or GUI presented by either windows or ubuntu ? In order for ubuntu (or any other o/s) to be used on a machine along with windows, a special utility called a super grub ( grand unified uinversal booter?) is written to the first sector of your first hard disk - hd0 during installation. Grub is given control first when your machine is booted. It should examine the various partitions on your machine and present you with a list of which o/s partitions you can boot from.

---

### Post by mellamopobrede on 2007-08-21
It might be your CD or CD-Drive.  I had similar problems and i switched to a different CD Drive and it worked fine for me.  Also, when you burn your cd, try to burn at a lower speed like 4X or 8X.

---

### Post by kedmond on 2007-08-21
No, it has nothing to do with Grub.  I can still boot to windows.  This is the menu that the XLive CD is supposed to show when you boot from the CD.  I cannot launch Ubuntu, however.  But I can boot Windows XP.

-kedmond

---

