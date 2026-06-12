---
title: "grub - load .iso after luks password"
date: 2014-07-09
forum: General Help
---

### Post by nekomata2 on 2014-07-09
Hello,
is it possible to load a .iso as alternative linux os (on grub) after I type my luks password? The iso would be located in the home folder, that is encrypted with luks, only /boot is unencrypted but it is too small to allocate the .iso

---

### Post by yancek on 2014-07-10
Do you mean you want to boot the iso file directly from Grub?  You can do that with Grub2 using a loopback entry or extracting the files and in both cases, manually putting a correct menuentry in the grub.cfg file.  Since your boot directory/partition needs to not be encrypted and you are going to be trying to boot the iso, I doubt it would work but no harm in trying.  I've never tried so I don't know.

---

### Post by nekomata2 on 2014-07-10
> **yancek said:**
> Do you mean you want to boot the iso file directly from Grub?  You can do that with Grub2 using a loopback entry or extracting the files and in both cases, manually putting a correct menuentry in the grub.cfg file.  Since your boot directory/partition needs to not be encrypted and you are going to be trying to boot the iso, I doubt it would work but no harm in trying.  I've never tried so I don't know.

Yes, but my /boot partition is too small for the .iso file, I need to store it in /home/linux.iso for e.g. but its encrypted so I need a way to load it after I type my luks password

---

### Post by yancek on 2014-07-10
The only way to find out is to try it.  Put the iso in your encrypted partition, put an entry in grub.cfg and try to boot.  If it doesn't work (I don't think it will but??) you simply remove the entry.  The other thing you may be able to do is resize your boot partition but that may be more trouble than it is worth.

---

### Post by nekomata2 on 2014-07-12
nope, im unsuccessful so far, can't boot an iso located inside an encrypted LVM :(

---

### Post by nekomata2 on 2014-07-25
bump

---

