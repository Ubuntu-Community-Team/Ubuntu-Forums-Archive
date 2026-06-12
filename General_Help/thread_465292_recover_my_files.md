---
title: "recover my files"
date: 2007-06-05
forum: General Help
---

### Post by ReaLitaliano on 2007-06-05
i installed ubuntu and something happened and now i cant boot to windows or linux and i just want my windows files back and i dont care about my Linux right now.No one was able to help me let.How can i recover my files back they r very important

---

### Post by taurus on 2007-06-05
Boot from the LiveCD and post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by muhdzuhri on 2007-06-05
just **fixmbr** using your xp cd.

---

### Post by ReaLitaliano on 2007-06-05
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by ReaLitaliano on 2007-06-05
if i use fixmbr that might mess things up

---

### Post by ReaLitaliano on 2007-06-05
whats the best way to do it with out losing anything?

---

### Post by ReaLitaliano on 2007-06-05
dont leave me hanging

---

### Post by muhdzuhri on 2007-06-05
ok,:popcorn: tell me what have been displayed on your monitor when you boot your computer?

---

### Post by ReaLitaliano on 2007-06-05
now i just get a black screen

---

### Post by ReaLitaliano on 2007-06-05
ok i just checked again to make sure and it says no active partition found

---

### Post by GuitarRocker2562 on 2007-06-05
fixmbr!

---

### Post by ReaLitaliano on 2007-06-05
everyone is saying that but will i lose my files is it safe

---

### Post by mainalisuyog on 2007-06-05
Yes, your files will be safe. just choose repair when u run the xp installation cd and when u get to the prompt, do fixmbr. It will just fix the master boot record so that XP can boot.

---

### Post by ReaLitaliano on 2007-06-05
well i tried it but still don't boot

---

