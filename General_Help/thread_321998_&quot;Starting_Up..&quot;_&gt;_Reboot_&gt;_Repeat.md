---
title: "&quot;Starting Up..&quot; &gt; Reboot &gt; Repeat"
date: 2006-12-19
forum: General Help
---

### Post by calx on 2006-12-19
Today when booting into Ubuntu I got the message: "Starting Up...." then a black screen, then the machine reboots and repeats the process. Im using GRUB to dual boot Edgy & XP, Windows is still booting ok. There doesn't seem to be any other error messages, unless my screen is blanking too quickly or for too long.

Immediately before this started to happen, Ubuntu had failed to boot past the the initial splash screen, I hit the reset button and the above problem started. Somethings corrupted I guess, but where should I start looking?

Thanks for any tips or links, im at a loss as to where to start.

---

### Post by mayonaise15 on 2006-12-20
Are you using an NVidia card?  There was a kernel update released a few days ago that killed some systems.  [Check out this thread]("http://ubuntuforums.org/showthread.php?t=318206") for more info.

---

### Post by calx on 2006-12-20
Nah it's an ATI unfortunately. Thanks though.

---

### Post by MFonville on 2007-12-22
I got the same problem here with a Pentium 3 with a Matrox G400.
Any idea how to solve this? it is a very big frustration not being able to boot... :S

---

### Post by torgrot on 2007-12-22
Try adding pci=biosirq acpi=off to your grub command line.  Hit esc when the menu come up and cursor to the line to boot ubuntu and press e to edit cursor down to the boot line and press e to edit again hit the end key and add that to the end of the line press enter and then b to boot.  If you have hyper threaded processor change acpi=off ot acpi=ht to enable the hyper threading.  You can then edit menu.lst and add them to the options.

torgrot

---

### Post by MFonville on 2007-12-23
adding those options doesn't solve the problem (i am using the hardy kernel btw, I tried the generic, server and 386 version and none of them worked)
Any other ideas? Or should I try a gutsy kernel?

---

### Post by clubsoda on 2007-12-24
Hi MFonville,
I recommend you try the Matrox G-series driver from [http://matrox.tuxx-home.at](http://matrox.tuxx-home.at) 
[This thread](http://ubuntuforums.org/showthread.php?t=629633) might help if you need further details.  Please post back if this works,
Cheers.

---

