---
title: "dvd playing not smooth"
date: 2005-04-09
forum: General Help
---

### Post by IdoMcFly on 2005-04-09
I'm using VLC to read DVD but the playing is quite ugly : it's like my system is lagging but I have an AMD64 CPU and 512Mo RAM.

I have an nvidia card with the nvidia drivers on.
Am I missing something ? :-s

---

### Post by IdoMcFly on 2005-04-09
forget me... I forgot to restore my DMA settings...

---

### Post by dusu on 2005-04-09
Did you try enabling dma ?
If your dvd-rom is /dev/hdc, type :
```
sudo hdparm -d1 /dev/hdc
```

---

