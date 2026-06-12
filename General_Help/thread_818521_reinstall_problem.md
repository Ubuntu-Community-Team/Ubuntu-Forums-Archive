---
title: "reinstall problem"
date: 2008-06-04
forum: General Help
---

### Post by bmck on 2008-06-04
i dual-boot vista and ubuntu and i "attempted" to reinstall a new copy of ubuntu 8.04 over the existing copy but im sure i didnt do it correct i dont remember the exact way i did all i remember is in the partition setup i think i deleted the ext3 partition and checked it and just hit forward. all i know now is when grub loads i get double all the boot options:

/boot$ ls
abi-2.6.24-16-generic             initrd.img-2.6.24-18-generic
abi-2.6.24-18-generic             initrd.img-2.6.24-18-generic.bak
config-2.6.24-16-generic          memtest86+.bin
config-2.6.24-18-generic          System.map-2.6.24-16-generic
grub                              System.map-2.6.24-18-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-18-generic

i can boot up and everything im not really sure what i need to do to solve this

---

### Post by Het Irv on 2008-06-04
```
gedit /boot/grub/menu.lst
```

Can you paste the output of this?
That will show exactly what is shown in the Grub menu when you boot.

---

