---
title: "Convert DVD/CD to any format with less size"
date: 2007-12-07
forum: General Help
---

### Post by Garcia_123 on 2007-12-07
movie? Could anyone please tell me which software is the best to use to rip DVD or CD and convert into WMV format in very less size and without affecting the quality of the Please let me know of a good converter which is the best you have tried. It does not matter if it is free or not, I will pay. Your help will be highly appreciated.
Thanks in advance!

---

### Post by ajopaul on 2007-12-07
You can rip dvd to avi with xvid codec, here's a 2 pass xvid encoding using mencoder.


```
$mencoder inputfile.VOB -oac mp3lame -ovc xvid -xvidencopts pass=1 -o /dev/null
``` ```
$mencoder inputfile.VOB -oac mp3lame -ovc xvid -xvidencopts pass=2:bitrate=1000 -o output.avi
```

---

