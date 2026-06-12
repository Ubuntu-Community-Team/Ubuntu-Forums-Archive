---
title: "Dual boot: how to change default OS in startup device menu?"
date: 2018-03-19
forum: General Help
---

### Post by elsa2 on 2018-03-19
Hello,

For some reasons my computer starts under Windows for the moment and I would like to set Ubuntu as default OS. I tried to change it through GRUB but it doesn't help, because it starts on Windows even before the GRUB menu - at the moment i see the startup device menu. Basically, if I don't push F12 and select ubuntu (which is the second line) my computer starts on Windows.
Picture hereby.

Thanks for your help!!

[[IMG]https://preview.ibb.co/kiUVKc/photo_2018_03_19_23_14_36.jpg[/IMG]]("https://ibb.co/b6WzCx")

---

### Post by Mark Phelps on 2018-03-19
That is neither a GRUB nor Windows menu; instead, that looks like a BIOS menu -- and in the BIOS, you can only select the boot order of devices, not partitions contained on those devices.

---

### Post by elsa2 on 2018-03-20
Indeed, thanks, the problem is solved!

---

### Post by yancek on 2018-03-20
Glad you got it solved.  The general method to change the boot order from an Ubuntu/Linux EFI system, log into a terminal and as root (sudo) user run this command and not the output:

```
sudo efibootmgr
```

You will see output similar to that below:

```

BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0003,0000,2001,2002,2004
Boot0000* Notebook Hard Drive - TOSHIBA MQ01ABD100
Boot0001* ubuntu

```

The output above shows 0001/ubuntu as first in boot order so it's boot menu should show on boot.  If you wanted to change to another, say 0003, you could use the command below:

```
sudo efibootmgr - 0003
```

You can add other entries by the 4 digit number to order them with  commas separating each set of numbers.

---

