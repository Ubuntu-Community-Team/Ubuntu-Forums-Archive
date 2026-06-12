---
title: "Can't rename SD card"
date: 2015-12-25
forum: General Help
---

### Post by RogerDavis on 2015-12-25
I have come to the conclusion that only Harry Potter himself can accomplish this.  

If I try with XFE, I get "Resource temporarily unavailable"

If I try with Terminal, I get "roger@roger-desktop:~$  sudo mlabel -i /media/roger/3637-6337 -s ::
Can't open /media/roger/3637-6337: Is a directory"

If I try Disks, 7.9GB Drive..., edit filesystem, change filesystem label, I get     "Cannot change label on mounted device of type filesystem:vfat.
 (udisks-error-quark, 11)"   BUT how the #%^&%^&*% do I see it if I unmount it???

Of course, ALL was done using SUDO.

Of course, I've tried 8 characters or less, and all upper case.

I've spent about 2.5 hours searching the web and other resources.  Not one valid direction.

Yes, it is unlocked and writeable.

Does ANYONE know how to do this?  Or is it truly impossible, and I have to use Windoze to accomplish it in 1 minute or less?

Thanks!

---

### Post by yoshii on 2015-12-25
Try using gParted to unmount the card's drive and then to set the label (name).  
I think renaming a drive is a drive type of command and it can't do it while the drive is in use and mounted.  
You have to unmount the drive first.  You don't have to eject it, but you do have to unmount it.  Mounting a drive is the system's way of gaining exclusive access to it to read and write from it.  
gParted has both the commands and you can also reformat quickly too if you need to.

If you have Lubuntu, you have to download and install gParted since it comes with Disks instead.

---

### Post by RogerDavis on 2015-12-25
It worked!

---

