---
title: "Fonts disappearing and segfaults"
date: 2008-06-14
forum: General Help
---

### Post by machuidel on 2008-06-14
Hello. I've got a problem with fonts disappearing (sometimes replaced with cube symbols), corrupt icons (not very often) and segfaults. This happens pretty often usually after opening new windows and typing inside fields. The problem then occurs on the entire desktop.
This also seems to only happen with programs using more advanced font rendering. Xterm for example survives.

I am using the following setup:
Software: Ubuntu 8.04 with all latest updates applied.
Motherboard: ECS M825G, Chipset: VT8378 [KM400/A]
Processor: AMD Athlon(tm) XP 2200+
Memory: Kingston ValueRAM 512mb DDR
Soundcard: Creative Labs SB Live! EMU10k1
Videocard: Nvidia GeForce 6200 (NV44A)

Already tried the following without any luck:
- Disabling onboard soundcard by not loading the driver (disable in BIOS does not seem to work).
- Reinstalling fontconfig and let it regenerate all the caches.
- Removing PCI soundcard and videocard only using the onboard hardware.
- Trying different RAM.

This problem also occurs when using the LiveCD.
MS Windows XP seems to run fine.

I've included some straces as attachments.

Thank you in advance ;)

---

