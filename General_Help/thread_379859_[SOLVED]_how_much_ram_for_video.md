---
title: "[SOLVED] how much ram for video?"
date: 2007-03-08
forum: General Help
---

### Post by saul_2110 on 2007-03-08
Hi. How do I know how much memory is assigned to video? [giving that video ram and main ram is shared]
Thanks.

---

### Post by Kateikyoushi on 2007-03-08
You know how much ram the system has, display the avaible maximum with "free" then you can count how much is assigned to video.

---

### Post by saul_2110 on 2007-03-09
Well, so I did and the answer was this one:

             total       used       free     shared    buffers     cached
Mem:           240        236          4          0          3         67
-/+ buffers/cache:        165         75
Swap:          258         17        241

I have a dimm of 256MB but then, it mean 16MB are assigned to video but in Bios, there are 64MB assigned to video. Any idea why?
Thanks.

---

### Post by Kateikyoushi on 2007-03-09
It can be set in xorg.conf as well, I guess more ins't needed.

---

