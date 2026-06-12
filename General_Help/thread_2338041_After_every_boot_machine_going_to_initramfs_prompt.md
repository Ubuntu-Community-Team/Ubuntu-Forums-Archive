---
title: "After every boot machine going to initramfs prompt"
date: 2016-09-24
forum: General Help
---

### Post by dhiru.zammer on 2016-09-24
While ubuntu update my machine got stuck. I started my machine in
recovery mode from then onwards I am not able to go to my normal os desktop. Now whenever I am starting my machine recovery mode option is coming and after that it is going to initramfs prompt terminal. Please guide me how I can go to my normal desktop. 
Here is my boot-info paste.ubuntu.com/23223487/

---

### Post by ian-weisser on 2016-09-26
Did you try any of the suggestions starting on Line 1521 of your boot-info?

---

### Post by ventrical on 2016-09-28
fsck /dev/sda1

at prompt.

do yes , yes , yes .. to all.

---

