---
title: "graphics info?"
date: 2007-12-27
forum: General Help
---

### Post by skymera on 2007-12-27
is there something similar to ```
 cat /proc/cpuinfo 
``` for graphics chips/cards?

ineed to know the exact name of mine and cant figure how.

thanks :)

---

### Post by zero-9376 on 2007-12-27
not sure if it is what you are looking for but system>preferences>hardware information might give you the required info

---

### Post by taurus on 2007-12-27
Maybe *lspci*?

---

### Post by chewearn on 2007-12-27
Look into /proc/driver directory.

E.g. mine:
$ cat /proc/driver/nvidia/cards/0
Model:           GeForce 6150
IRQ:             16
Video BIOS:      05.51.28.39.00
Card Type:       PCI
DMA Size:        39 bits
DMA Mask:        0x7fffffffff
Bus Location:    00.05.0

---

### Post by jken146 on 2007-12-27
lshw usually tells you a lot.

---

### Post by skymera on 2007-12-27
ok 4 ways of looking, i do now :)

and wha im trying tofind is he exact name

i know its S3 Unichrome Pro VGA.. but there is a number like VX6550 blah blah.

---

### Post by judepereira on 2008-01-04
try 'lspci' in the terminal. post me what you get

---

