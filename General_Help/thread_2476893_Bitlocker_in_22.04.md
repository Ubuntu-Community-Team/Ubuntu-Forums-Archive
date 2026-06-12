---
title: "Bitlocker in 22.04"
date: 2022-07-11
forum: General Help
---

### Post by my1 on 2022-07-11
so apparently there's native Bitlocker Supoort in (k)ubuntu now which is awesome, one question that remains for me is how to automount it tho. I have seen solutions from the past using dislocker but as there is a solution for mounting bitlocker in the system already I wonder if there's also a way to do that, and I could essentially put the bitlocker code into the /etc/fstab or whatever (obviously the linux is encrypted as well) and just mount it directly at boot.

also I have noticed 2 issues in the bitlocker implementation:

1) "save password" does not seem to save the password
2) it only shows the physical disk name that has the bitlocker partition, no partition label/number/id/whatever, and also not the bitlocker identifier, which would be pretty useful when it spawns 5 bitlocker prompts of which 3 are partitions on the same disk.

---

