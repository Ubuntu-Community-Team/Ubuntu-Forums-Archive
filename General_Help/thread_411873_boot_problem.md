---
title: "boot problem"
date: 2007-04-17
forum: General Help
---

### Post by g_monkey on 2007-04-17
heres the dealio,
i have my hdd setup to dual boot xp and ubuntu all was good, i formatted the windows partiton, /dev/sda1, now it just boots straight into xp, no boot options, how do i get it back so i can choose?

---

### Post by dfreer on 2007-04-17
it boots straight into XP AFTER you formatted the windows partition? *confused*

well whatever you did, you can use a live CD to reinstall grub.

[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

---

### Post by g_monkey on 2007-04-17
yee i was confused too, i assumed it would make no odds o well cheers for that ill give it a whirl

---

### Post by g_monkey on 2007-04-17
no luck there unfortunately, i booted from the cd, opened a terminal, when i do

```
grub
```

thats ok i get grub>, then i type

```
root (hd0.0)
```

and i get **Error 11: Unrecognized device string**

any ideas?

scrap all that fixed it

---

