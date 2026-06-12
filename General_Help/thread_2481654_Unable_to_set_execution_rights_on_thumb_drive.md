---
title: "Unable to set execution rights on thumb drive?"
date: 2022-12-05
forum: General Help
---

### Post by ne29914 on 2022-12-05
I have a script/batch file that I'd like to run from a thumb drive, but I'm not able to set the x bit. The sudo chmod u+x file command is simply ignored.
Copying the file to my HDD and doing the operation works fine.
Is there some kind of OS mechanism at work here? Perhaps some security thing?

Thanks.

---

### Post by guiverc on 2022-12-05
You've given no clues as to the *file-system* that exists on the thumb-drive.

The file-system bits (what is changed with `chmod +x`) may not exist on the file-system, thus the command may run, but the effects cannot be stored.  ie. is it a *ext4* system which can store those bits? or something like *vfat* or *ntfs* which by design store bits differently. The media (*ie. thumb-drive*) doesn't make any difference, but the file-system (*how it was formatted*) does.  I suspect this is what you're missing.

---

### Post by ne29914 on 2022-12-05
Sorry, sorry, sorry!!
Major brain fart on my side.
The USB drive was FAT. All works now, please ignore.

Thanks.

---

