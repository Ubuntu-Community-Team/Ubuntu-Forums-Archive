---
title: "Broke my ubuntu with usermod"
date: 2007-12-04
forum: General Help
---

### Post by karnival8 on 2007-12-04
i broke my ubuntu using

sudo usermod -G root username

how do i fix this? i heard i have to reboot, stall GRUB with esc and log in as root...

but then what?


thanks
r

---

### Post by bingoUV on 2007-12-05
After logging in as root, 
```

usermod -G username username

```

---

