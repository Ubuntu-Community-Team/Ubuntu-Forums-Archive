---
title: "How to add a DVD-drive-entry to Grub?"
date: 2007-05-17
forum: General Help
---

### Post by f0rc3 on 2007-05-17
Hi!

Is it possible to add a new entry to Grub in the menu.lst-file which would boot a DVD or CD?

I tried expressions like root (hdc,0), root (hdc), root (cdrom), root (cdrom0) and (root (cdrom0,0), but everything did not work...

Do you know how to make this work??

Thanks,

Force

---

### Post by IgnorantGuru on 2007-05-18
> **f0rc3 said:**
> Hi!

Is it possible to add a new entry to Grub in the menu.lst-file which would boot a DVD or CD?

I have seen this done but I think it involved using an image which in turn booted the CDROM (aka chainloading).

> Do you know how to make this work??

No, but I'm sure you can find howto's on it.

---

### Post by f0rc3 on 2007-05-18
> **IgnorantGuru said:**
> I have seen this done but I think it involved using an image which in turn booted the CDROM (aka chainloading).



No, but I'm sure you can find howto's on it.



That would be great :)

Thanks!

---

### Post by f0rc3 on 2007-08-20
I found a Tutorial how to add an entry to boot from CD/DVD:

[http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html](http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html)



Works perfectly :)

---

