---
title: "HELP. Friends computer and Grub Error 21"
date: 2007-10-20
forum: General Help
---

### Post by kevCast on 2007-10-20
Hello. My friend was interested in putting Ubuntu on a 10.0 Western Digital hardrive. He had two hardrives, the 10.0 GB and a 40.0 GB Seagate. When we first tried to install Ubuntu, the 10.0 was slave and the 40.0 GB one was primary. We tried to it on the 10.0 GB while it was on slave, installed, and got Grub Error 21. We then switched the 10.0 GB to Primary and the 40.0 GB to slave, reinstalled Ubuntu on the 10.0 GB, and the error was gone and we were faced with a dual boot option. It booted into Ubuntu fine, but when we tried to boot into Windows, it gave us Error 21. What's going on? Please help, I feel terrible for doing this to a friends PC.

---

### Post by kevCast on 2007-10-20
His entire family hates me. Please, anyone, help.

---

### Post by meierfra on 2007-10-20
Probably you just have to edit menu.lst. Post the output of 

```
cat /boot/grub/menu.lst
```

and 

```
sudo fdisk -l 
```

(both l are lowercase L)

---

### Post by confused57 on 2007-10-20
You also might want to go into your bios setup and make sure the IDE slave drive controller is set to "Auto" or possibly "On".

---

