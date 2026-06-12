---
title: "Formatting floppy to 1.72MB?"
date: 2006-08-16
forum: General Help
---

### Post by Just4 on 2006-08-16
I need to format a floppy to 1.72MB, is there anyways I can? I know it can be done but the command I was given doesn't work.

---

### Post by zxee on 2006-08-16
If you're trying to get a bootable image on the floppy the way to do that is:
> dd if=initrd.img of=/dev/fd0 Note: replace initrd.img with the actaual name&location of the file. Formatting isn't necessary because the above command will overwrite whatevers on the disk.

---

