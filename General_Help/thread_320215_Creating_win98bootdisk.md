---
title: "Creating win98bootdisk"
date: 2006-12-16
forum: General Help
---

### Post by Tekovro on 2006-12-16
im tying to create a win 98 boot disk. i downloaded the exe from bootdisk.com but when i try to open it i get the error saying  "the current image format is not supported by the disk drive"
i have the floppy in the floppy drive and it's clean.

---

### Post by hikaricore on 2006-12-17
You will need to find a .img file for the boot disk and use "dd" to write the image to a disk.

```
dd if=~/Desktop/win98.img of=/dev/fd0
```

This assumes the img file is on your Desktop, and your floppy drive is /dev/fd0.

Hope this helps.

--Aaron

[B]P.S.  I should also mention that you need to use dd with EXTREME caution,
it will happily overwrite any drive you point it at without confirmation.  I managed
to do this once about a year ago while I was drunk, overwrote my entire file system
with a floppy disk image.  rofl  It was funny about a half hour later when I reinstalled :P[/B]

---

