---
title: "[SOLVED] Ubuntu partition increase."
date: 2008-03-09
forum: General Help
---

### Post by Rytron on 2008-03-09
This is a theoretical question.
I have a dual boot pc-Ubuntu, Windows Xp on a 500gb hdd. Each os has approximately half of the total hdd space each.
If I was to get rid of Xp sometime in the future - could I allocate the partition that windows was occuping to Ubuntu so that I'd have one 500gb hdd? Alternatively would it be better to format the Windows partiton ti ext3 and could I then use this new ext3 partition from my Ubuntu boot?

I know its a long question. I'd appreciate any valid suggestions. Thank you.

---

### Post by scragar on 2008-03-09
you cannot resize partitions in use, so you would need to use the live CD to resize you ubuntu partition. if that option is not available then you will have to do as you suggested, and just reformat the windows partition and mount it from ubuntu to be able to use it's extra space.

---

### Post by Pumalite on 2008-03-09
You could do either one. Use Gparted Live CD and backup first.

---

