---
title: "wubi install."
date: 2007-12-13
forum: General Help
---

### Post by greythorne on 2007-12-13
Hello,

Just downloaded the wubi  installer, double clicked and the install began but when it comes to downloading the ubuntu-7.10 iso it downloads the AMD64 variant but mine is an intel P4 processor plus the transfer rate is terrible slow at 7kb/s. My broadband connection is at 6mb/s at this rate it will take around 24hours to complete the transfer!!

Any idea how to specify an alternate download location or is it possible to download the iso and point the installer to the location of the downloaded iso?

Thank you.

---

### Post by jokeas on 2007-12-13
Hey, you can find the answer right here: [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

"Note that 7.10 requires the DESKTOP ISO, you can download it manually and place it in the same folder containing the Wubi executable."

Although I'm unable to do "offline" install - wubi still needs something from internet and tries to connect to different servers. Probably the problem is proxy server i'm sitting behind, but I don't have any problems with other applications.

---

### Post by ago on 2007-12-13
Download the ISO and put it in the same folder as wubi.exe
Are you sure you do not have a dual core cpu? All 64 bits (including intel) use the AMD ISO.

---

### Post by greythorne on 2007-12-13
> **ago said:**
> Download the ISO and put it in the same folder as wubi.exe
Are you sure you do not have a dual core cpu? All 64 bits (including intel) use the AMD ISO.

Nope mine is P4 w/HT but upon checking with CPU-Z, the cpu instructions i have is EMT64 perhaps its because of this that wubi downloads the AMD64 version.

Thank you.

---

### Post by greythorne on 2007-12-15
Ok when i install wubi-7.10 alpha it just goes on saying "cramfs:wrong size". Now what in the world is that suppose to mean?

Thnks

---

### Post by dr_gauravsuneja on 2007-12-17
i have ubuntu iso on my desktop named ubuntu7.10-alternate-i386.iso but wubi when it installs even if the iso is in wubi folder doesn' t get recognised by wubi

---

### Post by Sanijs on 2007-12-17
Download ubuntu7.10-desktop-i386.iso it works for me!

---

### Post by ago on 2007-12-17
You can start wubi with --32bits flag to force a 32 bit iso
If the ISO is corrupted, wubi tries to download it again

---

