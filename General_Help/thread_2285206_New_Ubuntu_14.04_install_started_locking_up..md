---
title: "New Ubuntu 14.04 install started locking up."
date: 2015-07-03
forum: General Help
---

### Post by J_Gregory on 2015-07-03
Hi. New here. I have a Dell E521 with Ubuntu 14.04 installed. It ran ok for a couple of days, then started locking up when getting to login screen. Will not go any further. Sometimes the screen pixelates and goes diagonal. I can get into anything prior to login screen (CTRL+ALT+F1, BIOS) but I don't see any action, like when I boot into failsafe. I get a screen (with no cursor at all) saying system in low graphics mode and telling me to configure manually. But nothing works, keyboard or mouse. I have loaded 15.04 on a usb drive but even if I go into BIOS or go into setup and choose boot order, nothing works.

---

### Post by Geoffrey_Arndt on 2015-07-04
Have you installed the nvidia drivers via Systems Settings>Software & Updates>Additional Drivers (Tab)? . . . if you can use current gui at all , that's what should be done.   If gui desktop not available (black screen) etc., you will need to modify the PC's boot-up with the "nomodeset" option. (that will give you capability to navigate to additional drivers screen for download and install.

---

### Post by Bucky Ball on 2015-07-04
Welcome. Did you install third-party video drivers and have since done and update by any chance?

Could you boot the machine, get to the list of kernels to boot, highlight your regular kernel and hit 'e' to edit it.

Find the line that ends in 'quiet splash' or one or both of those words. At the end, after a space, add 'nomodeset', so it looks like this at the end of that line:

quiet splash nomodset

Follow the instructions at the bottom of the screen to save and continue (control+x and 'b' from memory). Any luck? If so, we'll have to figure out how it dropped the correct driver if it was working before. That's puzzling. :-k

I will say this: from the symptoms you describe sounds like a graphics issue.

PS: Just read Geoffrey_Arndt's post. Yes, try nomodeset option, but I only half agree with the rest. The Nvidia driver could be wrong and the reason this is happening. My money is on an update causing the driver to break, though, and yes, it could be a matter of reinstalling the driver if you installed it manually (an update generally won't break the drivers installed via Additional Drivers).

---

