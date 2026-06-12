---
title: "Gparted is a piece of crap"
date: 2007-02-02
forum: General Help
---

### Post by battleroyalex on 2007-02-02
It never works, always freezing when resizing my partition. Happens on many pcs and yes I have the space. Is there an open source program for WINDOWS that allows me to resize nfts partitions?

---

### Post by K.Mandla on 2007-02-02
(Edit: Scratch that; misread the post.)

---

### Post by aysiu on 2007-02-02
I'd highly recommend [PCLinuxOS's DiskDrake.](http://www.ubuntuforums.org/showthread.php?t=114142) DiskDrake's never given me any problems (unlike GParted and QTParted).

---

### Post by russell.h on 2007-02-02
My understanding is that you can't mess with mounted partitions, so if you find a partition editor in windows you still won't be able to mess with any partition that you can't make windows unmount (I have no idea how windows handles that).

---

### Post by battleroyalex on 2007-02-02
I figured it out. Most laptops have a wierd unallocated partiton size that is around 8mb and locked. I have 2 laptops with this and this is why i was getting the error

If you do CHKDSK /f in windows command prompt it should fix it

---

### Post by Polygon on 2007-02-02
was going to say, ive never had problems with gparted. However, qtparted does give me random errors when i try to resize partitons...

---

### Post by jeremy on 2007-02-03
> **battleroyalex said:**
> I figured it out. Most laptops have a wierd unallocated partiton size that is around 8mb and locked. I have 2 laptops with this and this is why i was getting the error

If you do CHKDSK /f in windows command prompt it should fix it

Does that mean that Gparted is a piece of crap no more?

---

