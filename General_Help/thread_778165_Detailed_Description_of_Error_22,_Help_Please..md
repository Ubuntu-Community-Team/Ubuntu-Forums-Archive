---
title: "Detailed Description of Error 22, Help Please."
date: 2008-05-01
forum: General Help
---

### Post by Xsnip3rX on 2008-05-01
Hello, I've recently installed Ubuntu 8.04 'Hardy' using the Ubuntu Live CD that i downloaded from the Ubuntu Website, I've installed it inside of Windows, and whenever i boot up, i placed it on my D: Drive by the way, Whenever i boot up, i get this Error Message:

```
Warning: Unrecognized Partition table for drive 82. Please rebuild it using a Microsoft-Compatible FDISK tool(err=28). Current C/H/S=122/255/63
Press 'esc' to enter the menu.
```
I press enter and this pops up.
```
Booting 'Ubuntu 8.04, Kernel 2.6.24-16-Generic'
Root (hd1,4)/Ubuntu/disks
Error 22: No such Partition
Press any key to continue
```

Any ideas? thanks.

`Kenny

---

### Post by ago on 2008-05-02
Try to follow these instructions: [https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by Xsnip3rX on 2008-05-03
Actually, i have, and for some reason it still does not work... is there a better or easier way to do this? i may have messed up on it.

---

### Post by ago on 2008-05-03
It could be that you need to fix your partition table first

---

### Post by tinybit on 2008-05-03
> 
root (hd1,4)/Ubuntu/disks
Error 22: No such Partition


To fix the issue, try to replace it with

```

root  ()/Ubuntu/disks

```

in your menu.lst file.

---

### Post by Xsnip3rX on 2008-05-03
Thanks are sent to both Tinybit and Ago for your help, Ultimately, TinyBit's post helped the most, i'm actually using Ubuntu right now.

---

