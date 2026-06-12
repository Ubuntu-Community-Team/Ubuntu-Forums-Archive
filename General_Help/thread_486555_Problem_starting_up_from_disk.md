---
title: "Problem starting up from disk"
date: 2007-06-28
forum: General Help
---

### Post by gothikar on 2007-06-28
Hello, I just got the Ubuntu iso and burned it to a disk. Now when I put the disk into my computer and let it boot to the cd, the main gui pops up asking me to select which option (start or install ubuntu, start ubuntu in safe graphics mode, ect...) and if i choose any option with default boot line it goes to just a black screen with a blinking _ and not text, however if i remove the "quiet splash" line from the boot line and load the first option which is the start or install ubuntu line, it shows that it is hanging at "[ 49.060573] ...TIMER: vector: 0x31 apic1=0 pin1=2 apic2=-1 pin2=-1", and I have also tried the safe graphics mode and it still hangs...Does anyone know why? My specs are:

MSI Motherboard 915p combo-fr
inter P4 3.2 ghz ht
2Gb of kingstom ddr2 533 ram
ati radeon x800xt GPU

any and all help will be appreciated.

Thanks a ton.

---

### Post by eggdeng on 2007-06-28
Have you tried  ```
boot noapic nolapic
```

---

