---
title: "Forced fsck on external drive slow."
date: 2007-08-19
forum: General Help
---

### Post by Novaoblivion on 2007-08-19
I just bought a 500gb WD My Book, formated it ext3, hooked up to my computer added it to fstab etc. I started up my computer and it says "/dev/sdc1 has gone 49709 days without being checked, check forced" and its taking forever! I am at 34.7% right now and its been about 2 hours it seems to freeze everytime it moves up a little. . I have had it force a check on me before for my internal drives and it was not nearly this bad. I saw a [similar problem]("http://ubuntuforums.org/showthread.php?t=483150") but it seems that the only solution (they found) was to turn off the checking which I dont really want to do. Thanks for any help.

---

### Post by band-aid on 2007-08-19
Does it try to check every time the machine boots up? If it does try removing the drive and plugging t in after its booted. It may be automounted as removable storage. This is just a guess though.

---

### Post by Novaoblivion on 2007-08-19
Nope just this time, it finally finished all total it took about 3 hours I think. It seemed to speed up towards the end.

---

### Post by Novaoblivion on 2007-08-19
I just had a sudden realization!  The computer is older and only has USB 1 ports. Does anyone know of a cheap but decent PCI usb 2.0 card that works well under Ubuntu? Thanks again sorry for the dumb question!

---

