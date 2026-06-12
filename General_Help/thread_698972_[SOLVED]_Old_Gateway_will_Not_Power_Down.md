---
title: "[SOLVED] Old Gateway will Not Power Down"
date: 2008-02-16
forum: General Help
---

### Post by LoSt180 on 2008-02-16
I have an old Gateway E-3200 that I'm bringing some new life into. I've upgraded the original 350MHz P2 to an 800MHz P3, and bumped the memory to 630MB. It's actually quite usable now with Ubuntu installed. 

My problem is that the Shut Down button does not actually Turn Off the computer. The Boot Up/Down Splash screen is not visible (monitor indicates "out of range", same problem on a Dell I have), so I'm not sure if there are any text warnings being displayed. Right now after Shut Down, I'll wait for the processor light to stop flashing and the keyboard lights will blink,  I can then push the power button to turn off the computer.

I had Fedora 7 installed at one point, and it DID turn off the computer. Does anybody have any clues? Is there anything I can list here to help out?

---

### Post by dvase on 2008-02-16
I really have no idea on the cause of your problem, however you could try powering down the system from the terminal using the "shutdown" command and see what happens.

---

### Post by LoSt180 on 2008-02-16
I typed 'shutdown -P now' in the terminal, no difference. Any other ideas?

---

### Post by dvase on 2008-02-17
You could try looking at the log messages from shutting down the machine.  I've never done this before myself but [this thread]("http://ubuntuforums.org/showthread.php?t=333278") seemed to give a few helpful hints.

---

### Post by oldos2er on 2008-02-17
This is a guess, but perhaps your computer uses APM instead of acpi. Ubuntu doesn't support APM by default, but you can install it through Synaptic.

---

### Post by LoSt180 on 2008-02-17
hmm, we might be on to something. When the computer boots up, it has a message that says something along the lines of: "BIOS date (1999), fails ACPI cutoff (2000). ACPI forced will be used"

I searched Synaptic for APM and found apmd is already installed. It's disabled by default, it says to "boot the kernel with the 'apm=on' option to enable the driver. (You may need to add this option to you lilo command line.)" Since Ubuntu uses GRUB, how would I enable this option?

---

### Post by LoSt180 on 2008-02-17
Thanks oldos2er, I wouldn't have guessed that the ACPI error was related to power management.

after searching around on the 'fails acpi cutoff, use acpi=force' error, I tried a few options..

I edited /boot/grub/menu.lst to include 'apm=on acpi=force' on the kernel line. 

I also added to the /etc/modules file:

apm power_off=1


It works now! It didn't work with just the 'apm=on' option, so I'm not sure if I can remove it and just use 'acpi=force'. I'm just happy I got the computer to shut down!

Edit: just did a fresh install of Hardy 8.04; I only had to add acpi=force to get the computer to shut off. I went ahead and put it in the first "default options" so that it will be automatically appended to future kernel updates.

---

### Post by oldos2er on 2008-02-17
Glad it worked!

---

