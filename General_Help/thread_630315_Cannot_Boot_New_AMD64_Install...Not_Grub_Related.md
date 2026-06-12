---
title: "Cannot Boot New AMD64 Install...Not Grub Related"
date: 2007-12-03
forum: General Help
---

### Post by PRGUY85 on 2007-12-03
Hello:

I am a longtime Ubuntu user.  Recently, I decided to have a fresh install of Gutsy AMD64 for my new CPU (Intel Core Duo).  The install went fine yet when I enter Grub and hit enter on the Gutsy option, the boot hangs...It shows some lines on the bottom left corner of the screen about Kernel alive or something and then the monitor goes to sleep while the computer is still on.  However, the PC is not making any hard drive noises so its apparently not doing anything.

Any ideas?

---

### Post by PRGUY85 on 2007-12-03
I edited Grub by deleting quiet and splash from the grub entry.  Linux began to load the hardware yet seems to hang on the CD part.  This is strange considering I was able to install Ubuntu using the same CD Drive without problems...

---

### Post by PRGUY85 on 2007-12-03
I now can enter the Ubuntu partition, however when I choose the WinXp partition the Grub hangs on Grub Stage 2 loading....and doesn't do anything else.

The WinXP partition is not accessible on Ubuntu either, saying it cannot be mounted and telling me that its not a valid NTFS partition.  When I use GParted, it says it IS a NTFS partition but doesn't allow me to access it...so is my WinXP partition hosed?

---

### Post by PRGUY85 on 2007-12-03
bump

---

