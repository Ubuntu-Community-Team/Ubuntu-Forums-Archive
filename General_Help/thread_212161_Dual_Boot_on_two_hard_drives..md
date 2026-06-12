---
title: "Dual Boot on two hard drives."
date: 2006-07-09
forum: General Help
---

### Post by PriceChild on 2006-07-09
Ok here we go, i've got Ubuntu installed on the master, windows on the slave.

Currently using the bios to choose which disk to boot off and have finally had enough.

However... the following in my /boot/grub/menu.lst doesn't work:

```
(snip)
title        Ubuntu, kernel 2.6.15-25-k7
(snip)

title        Ubuntu, kernel 2.6.15-25-k7 (recovery mode)
(snip)

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP
root        (hd1,0)
savedefault
makeactive
chainloader    +1

```

Can anyone point out the problem please?

Thanks, pricey

---

### Post by wyohermit on 2006-07-09
You have to fake windows into thinking it is on the master drive.
This worked for me.


title        Windows XP
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

---

### Post by PriceChild on 2006-07-09
Worked perfectly thanks! :)

---

