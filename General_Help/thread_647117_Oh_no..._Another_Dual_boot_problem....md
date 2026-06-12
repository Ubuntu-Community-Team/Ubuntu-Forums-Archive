---
title: "Oh no... Another Dual boot problem..."
date: 2007-12-22
forum: General Help
---

### Post by spiney_norm on 2007-12-22
Ok, A few days I accidently downloaded Ubuntu twice, I deleted the second one by getting rid of the partition then deleting it in the terminal. But now when I try to boot into windows from selection when I turn on my computer, it says something about "Not a bootable disk, Please insert a bootable floppy disk then press enter" or something like that. I'm pretty sure that when I was moving my partitions around I got rid of the windows one, is there still a way to boot back into Windows? Or by deleting the partition did I get rid of Windows.?

---

### Post by pyronaut on 2007-12-22
do u mean to say u installed ubuntu twice??

---

### Post by spiney_norm on 2007-12-22
yeah but i fixed that, deleted the second one.

---

### Post by meierfra on 2007-12-22
Open a terminal (Applications->Accessories->Terminal). 

Type 
```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

copy the output and post it here.

The "fdisk -l" information will tell us whether you deleted to Windows partition. "menu.lst" is need to figure out how to boot into windows (if it still exists)

---

### Post by Bothered on 2007-12-22
Sounds like you've deleted the ubuntu install to which the GRUB MBR was pointing. Something like:

Before:

MBR   --> Ubuntu 2

Windows

Ubuntu 1

Ubuntu 2



After:

MBR --> Empty or non-existent partition

Windows

Ubuntu 1

Empty or deleted


Follow the steps in the last post and someone should be able to give you instructions to reinstall GRUB.

---

