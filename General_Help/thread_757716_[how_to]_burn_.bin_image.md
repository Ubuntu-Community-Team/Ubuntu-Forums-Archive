---
title: "[how to] burn .bin image"
date: 2008-04-17
forum: General Help
---

### Post by tubunu on 2008-04-17
1. Install poweriso

```
$ wget http://poweriso.com/poweriso.tar.gz
$ sudo tar -zxvf poweriso.tar.gz -C /bin
$ rm -f poweriso.tar.gz
```

2. Run the program
```
poweriso
```

3. Execute command
```
poweriso convert /home/user/yourfile.bin -o /home/user/yourfile.iso -ot iso
```

4. Burn with your favourite burning app.

:KS

---

### Post by Trail on 2008-04-17
> sudo tar -zxvf poweriso.tar.gz -C /bin

Well, I would certainly not extract it there...

Acetone2iso has some pretty nice converting facilities within a GUI, by the way.

---

### Post by tubunu on 2008-04-21
> **Trail said:**
> Well, I would certainly not extract it there...

Why not?

---

