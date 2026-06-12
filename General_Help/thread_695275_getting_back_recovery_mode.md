---
title: "getting back recovery mode"
date: 2008-02-12
forum: General Help
---

### Post by linuxsux on 2008-02-12
so i run a class at a high school and i disabled recovery mode on all the computers but i want to enable it again but i don't know how. Can i get to recovery mode with a boot cd and how?

---

### Post by mbeierl on 2008-02-12
Make sure this is in /boot/grub/menu.lst
```

# altoptions=(recovery mode) single

```
and then re-run update-grub:
```

sudo update-grub

```
Lastly, change your moniker :)

---

