---
title: "Boot Loader?"
date: 2007-11-12
forum: General Help
---

### Post by RealEmotionX on 2007-11-12
Small issue.

I installed Windows XP (fresh) and Ubuntu 6.06 (fresh). I updated from 6.06 (I tried installing 7.10 but the installer hung at 46% in the partitioner. And I burned it at 2x speed even at that speed it ruined my CD-Rs). So I updated to 7.10, and the boot loader lists Ubuntu 7.10 Like 4 times. no real problem just a aesthetic annoyance.

---

### Post by zvacet on 2007-11-12
It is no problem at all.It is saying to you that you have to differnt kernels and both of them have recovery mode.

[http://ubuntuforums.org/showthread.php?t=585831&highlight=hide+kernel]("http://ubuntuforums.org/showthread.php?t=585831&highlight=hide+kernel")

---

### Post by namanbagga on 2007-11-12
Edit menu.lst using this command

```
sudo gedit /boot/grub/menu.lst
```

next to the entry you don't want to be visible place a # to the left of it

For eg to hide the recovery mode option-
convert this
```
title		Ubuntu 7.10,(recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=71-41dd-babd-278109f26a95 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

```

to 
```

#title		Ubuntu 7.10,(recovery mode)
#root		(hd0,8)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=71-41dd-babd-278109f26a95 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic
```

---

