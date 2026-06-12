---
title: "Had a System Encryption - Installed Ubuntu"
date: 2008-04-29
forum: General Help
---

### Post by Kenchu on 2008-04-29
I've got a laptop that used to have Windows on it, with a system encryption (and truecrypt boot loader). I decided to install Ubuntu on it instead, on the entire disk (single partition). Now when I boot the laptop, truecrypt boot loader is still there and I am unable to boot Ubuntu. Weird, since I thought grub would be installed, replacing truecrypt boot loader, but apparently not. Any help would be appreciated!

I've also asked this on the truecrypt forums (no answers yet), but thought it wouldn't hurt to ask here aswell.

Regards.

---

### Post by Rainstride on 2008-04-29
if you reformat the drive completely it should be fine.if you still want system encryption get the alt version of ubuntu and use the text setup and theres an option for an encrypted setup.

---

### Post by Kenchu on 2008-04-29
> **Rainstride said:**
> if you reformat the drive completely it should be fine.if you still want system encryption get the alt version of ubuntu and use the text setup and theres an option for an encrypted setup.

I'd be happy if I wouldn't have to reinstall ubuntu again, to save time. I have no intrest in keeping any system encryption.

... I thought ubuntu installer would format the disk. :p

---

### Post by Rainstride on 2008-04-29
the truecrypt boot loader is in the same place as the MBR as far as i remember witch means if you just used a partition and not the whole disk the boot load remains... im not sure what to do other than reinstall/format, but im sure there are people WAY BETTER with ubuntu on here than me that might have an idea.

---

### Post by Kenchu on 2008-04-29
> **Rainstride said:**
> the truecrypt boot loader is in the same place as the MBR as far as i remember witch means if you just used a partition and not the whole disk the boot load remains... im not sure what to do other than reinstall/format, but im sure there are people WAY BETTER with ubuntu on here than me that might have an idea.
I tried booting from the CD again, but chose to try ubuntu out, and installed it from there instead. Then it would overwrite the boot sector. So now it works.

---

