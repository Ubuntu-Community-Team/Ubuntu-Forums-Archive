---
title: "Flashing a floppy"
date: 2017-05-20
forum: General Help
---

### Post by warmango on 2017-05-20
i am relativelly new to ubuntu and was curious as to how i would SAFELY perform a RAW WRITE to a floppy disk (3.5in). i have the Dive installed and the floppy is reading as inserted, how would i do that?
 the string i found online to work im not to sure if it would safely work 

$ dd if=plpbt.img of=/media/zach/disk bs=1024 conv=sync ; sync

  plpbt.img is the PlopBoot Manager and the /media/zach/disk is the EXACT file path to the floppy disk from the root directory

---

