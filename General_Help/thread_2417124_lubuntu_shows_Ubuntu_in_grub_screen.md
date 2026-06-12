---
title: "lubuntu shows Ubuntu in grub screen"
date: 2019-04-21
forum: General Help
---

### Post by ben888 on 2019-04-21
I just dualbooted lubuntu and Windows 10. After successfully installing lubuntu, I changed boot BootOrder in bios, but it was 'ubuntu' in bios instead of lubuntu. And same in grub screen; it's showing Ubuntu instead of lubuntu and if I select Ubuntu,it's Booting into lubuntu itself. Previously I had Ubuntu installed. Is that's the reason? If yes, how to solve it?

---

### Post by mörgæs on 2019-04-21
Hi, welcome to the fora.

Seen from a BIOS perspective all Buntus are the same and they will be displayed as Ubuntu in the menu. 

A Buntu installation can have one or more desktop environments to choose from but this happens later in the boot process. 

Nothing to worry about. Sit back and enjoy.

---

### Post by Rubi1200 on 2019-04-21
Perhaps helpful if we can see the results from:

```
cat /etc/default/grub
```

and

```
sudo fdisk -l
```

Thanks.

---

### Post by coffeecat on 2019-04-21
Support, not chat.

*Thread moved to **General Help**.*

---

