---
title: "Resetting grub after separate distribution install"
date: 2008-06-14
forum: General Help
---

### Post by cclofton on 2008-06-14
Hello, I recently tried out 64 studio by installing it to a new partition, and it seemed to load up grub just fine. However, in my menu.lst file in ubuntu, 64 studio is not an option. Therefore I'm hesitant about formatting the 64 studio partition because it seems it has taken over grub, and if I format the partition I might lose access to ubuntu. So, what I'm looking for is a way to make sure that grub is using the ubuntu installation as default, not the 64 studio one.

Thanks

---

### Post by meierfra. on 2008-06-14
Click on FixGrub in my signature for instruction how to reinstall grub.

---

### Post by cclofton on 2008-06-14
Thanks for that. "find" gives me two results -  (hd0,3) & (hd0,4) - any way to tell which is which? Yeah I could just use trial and error, but....there's bound to be a better solution

Thanks again for the reply

---

### Post by meierfra. on 2008-06-14
(hd0,3) corresponds to /dev/sda4  (or /dev/hda4)
(hd0,4) corresponds  to /dev/sda5  (or /dev/hda5)

Boot into ubuntu, open a terminal and type

```
df / 
```

This will tell you whether Ubuntu is /dev/sda4 or /dev/sda5. Then just using the corresponding (hd0,?)

---

