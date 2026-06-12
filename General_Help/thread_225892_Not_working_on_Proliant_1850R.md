---
title: "Not working on Proliant 1850R"
date: 2006-07-30
forum: General Help
---

### Post by dcahrakos on 2006-07-30
Hi,
I cant seem to get Ubuntu to load on a Compaq Proliant 1850R.

Ive been trying since I got by cd's in the mail a week ago, but no luck.

I pop the cd in, it gets to the menu, so I put in some extra commands, since theres no usb, or acpi, and then hit enter...everything seems to go fine, until its done loading everything, and gets ready to load the desktop, then it just stays at a black screen. Ive let it stay there for 10,15 and 20 minutes, but nothing happens. 

on the CD sleeve, it says to install i have to load ubuntu, then double click on install, but is there any way I can install without having to go into the live cd first? just to see if that works.

Also, I cant get to any console or anything.

Has anyone been able to install this on a proliant? any special arguements I need to pass besides the usb, and acpi ones?

---

### Post by hw-tph on 2006-07-31
Try the alternate install CD. It is like the old Ubuntu installer, with a curses (semi-graphic) interface for the installer. There are alternate install CD's for x86, PPC and AMD64.


Håkan

---

### Post by dcahrakos on 2006-07-31
yeah, although this is the one I got from ordering it from shipit, I would rather not download it unless its for sure to work, and since this one doesnt work, im not sure how well that one will work....

anyone have any other suggestions?

---

### Post by devnull73 on 2006-08-10
I had the same problem, but with kubuntu dapper.

I ended up installing breezy, but there are many more problems to overcome: crashes from pressing certain keys, fans running at full speed all the time etc

I couldnt get the GUI going, but I wouldnt install X on a server anyway.

I might try the alternate install for dapper myself.

---

### Post by JL. DOLLAT on 2006-10-02
The messy thing in these machines is the USB sub-system. If there is no USB card plugged in any slot, no USB peripherals, just disable USB and USB-STORAGE:
- in the first stage during the installation process by passing arguments to the kernel "nousb" and "nousb-storage";
- in the second stage, once installation completes, BEFORE REBOOTING, switch to a console (<ctrl> <alt> <f2> for instance) and edit the file /boot/grub/menu.lst: add "nousb" "nousb-storage" (without the leading and trailing ") to the kernel arguments line.
There is more information about this problem somewhere else on the Net, which helped me set up one of those big and noisy engines, but I can't track it back now.
Hope it would help you

---

