---
title: "Where do i extract the.bin of realplayer to?"
date: 2006-12-27
forum: General Help
---

### Post by vikrant_me on 2006-12-27
I downloaded the realplayer bin and extracted it and it works great bt i want it to integrate with my system meaning when i type alt+f2 (run) and typerealplayer it says file not found so basically its extracted and woks frm tht folder bt has not been integrated well into the os

---

### Post by taurus on 2006-12-27
I would install it in /opt and near the end, it will ask you if you want it to link to /usr/bin, answer yes so realplay would be in your path...

---

### Post by vikrant_me on 2006-12-27
did that when i run real...it auto completes and shows me realplayer icon but it says :

Could not open location 'file:///realplay'

---

### Post by taurus on 2006-12-27
From a terminal, what's the output of this command?

```
whereis realplay
```

---

### Post by haiku99 on 2006-12-27
you need to type realplay, NOT realplayer....also if all else fails automatix2 can install RP, worked well for me...

---

