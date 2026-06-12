---
title: "Unable to boot from Ubuntu partition"
date: 2007-06-27
forum: General Help
---

### Post by cronco on 2007-06-27
Things are like this: I installed Ubuntu and afterwards open Suse on a different parittion, so from then on, the booting waws done from Suse's GRUB. But I don't use Suse almost at all so i want to get rid of it, so from Ubuntu GpartEd I switched the "boot" flag from hda4, which is Suse's partition to Ubuntu's hda1, but when I restart my computer, It says that my harddisk has "No operating system".

Any idea what's causing that?

---

### Post by dreadlord_chris on 2007-06-27
> **cronco said:**
> Things are like this: I installed Ubuntu and afterwards open Suse on a different parittion, so from then on, the booting waws done from Suse's GRUB. But I don't use Suse almost at all so i want to get rid of it, so from Ubuntu GpartEd I switched the "boot" flag from hda4, which is Suse's partition to Ubuntu's hda1, but when I restart my computer, It says that my harddisk has "No operating system".

Any idea what's causing that?

yup... since you installed SuSE 2nd it replaced your original (Ubuntu) GRUB. You are probably going to have to use your Ubuntu LiveCD (you still have it don't you?) to reinstall GRUB to your 1st partition. You can also use the GpartEd LiveCD to do this.

---

### Post by strabes on 2007-06-27
Yeah, you'll have to reinstall grub. See the link in my sig.

---

