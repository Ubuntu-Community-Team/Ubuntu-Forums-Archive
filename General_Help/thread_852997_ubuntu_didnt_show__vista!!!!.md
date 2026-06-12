---
title: "ubuntu didnt show  vista!!!!"
date: 2008-07-08
forum: General Help
---

### Post by nirvaanaa on 2008-07-08
hi everyone.
i have vista ultimate installed in one of the partition of my hd. yesterday i installed ubuntu 8.04 in another partition of same hd. now i cant boot into vista. in the boot menu windows vista was not shown. so i edited the menu.lst in grub in ubuntu. now the windows option was displayed yet i am still unable to log on to vista. my vista partition is not overwritten. any ideas. pls help. thank you.

---

### Post by Elfy on 2008-07-08
Can you post your menu list - open a terminal and do these and post results please

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

